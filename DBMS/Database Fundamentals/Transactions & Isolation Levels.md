## The Universal Problem: The Last Concert Ticket

I want you to feel this problem, not memorize it.

There is **one ticket left** for a concert.  
Two people—Alice and Bob—click “Buy” at the same time.

The database is the box office clerk.

Isolation levels decide **how disciplined that clerk is** when two hands reach for the same ticket.

Every concurrency bug you’ve ever seen is just a different version of this moment.

## The Concert Ticket Drama in Four Acts

### Setting the Stage

We have a table:
- tickets(id=1, available=1)

Two transactions:
- Transaction A (Alice)
- Transaction B (Bob)

Both want the same last ticket.

Now we replay the same moment four times, with four different rules.

### Act 1: Read Uncommitted — The Gossip Problem

In this world, the clerk **gossips**.

Alice starts buying the ticket.  
The clerk temporarily marks `available = 0` but hasn’t finished the sale yet.

Bob looks over the clerk’s shoulder and sees:  
“Looks sold.”

Bob walks away.

Then Alice’s transaction fails. Payment error.

Result:
- Ticket is actually still available
- Bob was incorrectly turned away

This is **Dirty Read**.

Bob saw **uncommitted truth**, like reading someone’s draft email and assuming it was sent.

Technical definition:
- Transactions can read data written by other transactions **that may later roll back**

Why this is dangerous:
- Decisions are made based on reality that never actually existed

PostgreSQL note:
- PostgreSQL **does not allow Read Uncommitted**
- It silently upgrades it to Read Committed
- That alone tells you how unsafe it is

### Act 2: Read Committed — The Changed Mind Problem

Now the clerk is more professional.

Bob can only see **committed** data.

Alice starts buying the ticket.  
Bob checks availability. He still sees `available = 1`.

Alice completes the purchase.  
Now the ticket is gone.

Bob checks again.  
Now he sees `available = 0`.

Bob saw **two different truths** within the same attempt.

This is **Non-Repeatable Read**.

The data changed between reads because someone else committed in between.

Technical definition:
- Each statement sees the latest committed data
- No guarantee that repeated reads return the same result

This is the default in PostgreSQL.

Why it’s acceptable:
- Most web apps tolerate changing data
- You refresh the page, things change—that’s reality

Why it can break logic:
- If your code assumes stability within a transaction, it will fail silently

### Act 3: Repeatable Read — The Moving Target Problem Solved

Now the clerk freezes time **for Bob**.

When Bob starts his transaction:
- The system takes a **snapshot**
- That snapshot never changes

Alice buys the ticket after Bob starts.

Bob checks availability again.  
He still sees `available = 1`.

The target is no longer moving.

This solves **Non-Repeatable Reads**.

But here’s the twist.

Bob tries to buy the ticket.  
The system says:  
“Sorry. Someone else already committed.”

Bob’s view was consistent, but not current.

Technical definition:
- All reads in a transaction see the same snapshot
- Writes may still conflict at commit time

PostgreSQL detail:
- Implemented via **MVCC snapshots**
- Reads don’t block writes
- Writes don’t block reads

This is why PostgreSQL scales so well under read-heavy load.

### Act 4: Serializable — The Perfect Orchestra

Now the clerk enforces **one logical order**.

Even if Alice and Bob click at the same time, the system guarantees:

- The outcome is identical to _some_ serial order
- As if one happened entirely before the other

One buyer wins.  
The other is forced to retry.

No illusions.  
No surprises.  
No anomalies.

Technical definition:
- Transactions behave as if executed one at a time
- The strongest isolation level

PostgreSQL reality:
- Uses Serializable Snapshot Isolation
- Detects dangerous patterns
- Aborts one transaction to preserve correctness

Cost:
- More retries
- Less concurrency
- More engineering discipline required

This is what you use when **overselling is unacceptable**.

## The Three Data Anomalies as Crime Scenes

Think like a detective.

### Dirty Read — The Open Case File

You read a case file while the detective is still writing notes.  
Later, the notes are thrown away.

You acted on fiction.

That’s Read Uncommitted.

### Non-Repeatable Read — The Shape-Shifting Evidence

You examine evidence.  
You turn around.  
You examine it again.  
It has changed.

Someone else altered it while you weren’t looking.

That’s Read Committed.

### Phantom Read — The Ghost Evidence

You count all tickets in section A.  
You count again.  
There are more rows than before.

New evidence appeared out of nowhere.

That’s the phantom problem.

Only Serializable fully prevents this.

## Isolation Levels as Security Clearances

Burn this hierarchy into memory.

Read Uncommitted:
- Public gossip
- You see drafts
- Fast, dangerous

Read Committed:
- Official announcements only
- No drafts
- PostgreSQL default

Repeatable Read:
- Classified snapshot
- Stable view
- Conflicts at commit

Serializable:
- Vault access
- One logical order
- Maximum safety, maximum cost

Once you see this ladder, you’ll never mix them up.

## Practical PostgreSQL Usage

Setting isolation level:
BEGIN TRANSACTION ISOLATION LEVEL READ COMMITTED;  
BEGIN TRANSACTION ISOLATION LEVEL REPEATABLE READ;  
BEGIN TRANSACTION ISOLATION LEVEL SERIALIZABLE;

What actually happens internally:
- PostgreSQL creates MVCC snapshots
- Each query checks visibility rules
- Serializable adds conflict detection on top

Performance intuition:
- Higher isolation = more bookkeeping
- More retries, not necessarily more locks
- Reads remain non-blocking due to MVCC

## The Memory Matrix (Describe It, Don’t Memorize It)

Imagine a grid.

Isolation level: Read Uncommitted

- Dirty Reads: Yes
- Non-Repeatable Reads: Yes
- Phantom Reads: Yes
- Performance: Fast, unsafe

Isolation level: Read Committed

- Dirty Reads: No
- Non-Repeatable Reads: Yes
- Phantom Reads: Yes
- Performance: Balanced

Isolation level: Repeatable Read

- Dirty Reads: No
- Non-Repeatable Reads: No
- Phantom Reads: Possible (implementation-dependent)
- Performance: Snapshot overhead

Isolation level: Serializable

- Dirty Reads: No
- Non-Repeatable Reads: No
- Phantom Reads: No
- Performance: Retries, contention

Visualize the grid once. You’ll recall it forever.

## MongoDB and Redis Through This Lens

### MongoDB

In MongoDB:

- Single-document operations are atomic
- Isolation is effectively document-level
- Multi-document transactions exist, but:
    - Higher overhead
    - Snapshot-based reads

Read concern:
- “local” can show data not yet majority-committed
- “majority” aligns closer to Read Committed semantics

MongoDB teaches you isolation through **document boundaries**.

### Redis

Redis is single-threaded.

That means:
- Commands execute one at a time
- Natural serializability at command level

But:
- No rollback
- MULTI/EXEC is not isolation, it’s batching
- Pipelines don’t protect invariants

Redis avoids isolation problems by **forbidding concurrency**, not by managing it.

Different philosophy, same lesson.

## Real-World Decision Framework

Use this in production.

1. Can you tolerate reading drafts?
    - If yes, Read Uncommitted (almost never)
2. Do you only care about committed data?
    - Read Committed (default for a reason)
3. Do calculations require stable inputs?
    - Repeatable Read
4. Must the outcome match a single-threaded world?
    - Serializable

Rule of thumb:
- Start at Read Committed
- Move to Repeatable Read for money
- Use Serializable when lawsuits are possible

## War Stories from the Field

Story one: Phantom inventory

An e-commerce system counted available items, then inserted orders.  
Under high concurrency, new rows appeared between reads.  
Overselling followed.

Fix:
- Serializable isolation
- Or explicit locking

Lesson:
- Phantoms are not theoretical. They ship bugs.

Story two: Lying dashboards

A reporting query ran at Read Uncommitted.  
Numbers changed mid-query.  
Executives lost trust in metrics.

Fix:
- Read Committed snapshot consistency

Lesson:
- Even reads can corrupt decision-making.

## The Isolation Mantra

Say this out loud:

“**Uncommitted sees all,  
Committed sees final,  
Repeatable sees stable,  
Serializable sees single.**”

Each line encodes:
- What you see
- What you don’t
- What you pay for it

## Isolation Intuition Exercises

Scenario:  
You calculate total balance, then apply interest.

Question:  
Which anomaly breaks you at Read Committed?

Answer:  
Non-repeatable read. Balance changes mid-calculation.

Scenario:  
You count seats, then insert reservations.

Question:  
Which anomaly breaks you at Repeatable Read?

Answer:  
Phantom reads.

Practice predicting the failure, not memorizing the fix.

## From Theory to Console

To test this yourself in PostgreSQL:
1. Open two psql sessions
2. Begin transactions at different isolation levels
3. Update and read the same rows
4. Watch visibility change

Once you _see_ it, isolation becomes instinct.

## Isolation Instincts

Isolation is the difference between **order and chaos** under concurrency.  
Every isolation level is a trade between **truth and throughput**.  
Once you understand the ticket clerk, you understand isolation everywhere.