Data structures can be broadly classified into two major categories:

- Linear data structures
- Non-linear data structures

Each category offers unique ways of organizing data based on how elements relate to one another.

## Linear data structures

Linear data structures arrange elements in a sequential, ordered manner where each item is positioned directly next to another. This allows data to be processed in a clearly defined order, making them intuitive and easy to implement for many common tasks. Their straightforward nature makes them ideal for scenarios where operations happen step-by-step, such as iterating through a list or managing tasks in a queue.

Because of their simplicity, linear data structures are often the first choice for programmers when handling collections of data. They provide predictable traversal, consistent performance for sequential access, and flexibility through both fixed-size and dynamically growing variants. These qualities make them widely applicable in day-to-day programming, from handling arrays of values to managing undo/redo operations using stacks.

**Key characteristics:**
- **Sequential organization**: Data elements are stored one after another in a specific order.
- **Single-level structure**: All elements exist on the same level, making traversal simple.
- **Efficient access in sequence**: Moving through elements is easy and predictable, especially for iteration-based tasks.
- **Fixed or dynamic size**: Some structures have a predefined size (like arrays), while others can grow or shrink as needed (like linked lists).

**Examples:** Arrays, linked lists, stacks, queues.

## Non-linear data structures

Non-linear data structures organize data in hierarchical or interconnected forms rather than following a single, straight sequence. This layout allows elements to branch out or link in multiple directions, creating richer and more flexible relationships among data points. Such structures excel in representing real-world systems where one-to-many or many-to-many relationships naturally occur, such as file systems, organizational charts, or transportation networks.

These structures enable efficient operations that are difficult or slow to achieve with linear systems, such as fast searching, hierarchical traversal, or exploring multiple paths within a network. Their flexibility makes them indispensable in areas like artificial intelligence, database indexing, graph algorithms, and decision-making systems. As data grows more complex, non-linear data structures become essential for maintaining both performance and scalability.

**Key Characteristics:**
- **Hierarchical or network-based layout**: Elements may have parent–child relationships or multiple connections.
- **Multiple traversal paths**: There is no single linear path; data can be accessed in many directions.
- **Efficient for complex data representation**: Ideal for scenarios like hierarchical storage, graph-based routes, or decision-making systems.
- **Flexible structure size**: Can grow in multiple directions without a fixed pattern.

**Examples:** Trees, graphs.

### Linear vs non-linear data structures

| Basis                           | Linear data structures                                                      | Non-linear data structures                                                      |
| ------------------------------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Definition**                  | Data elements are arranged sequentially, one after the other.               | Data elements are arranged hierarchically or in a non-sequential manner.        |
| **Memory allocation**           | Can use sequential memory (arrays) or dynamic memory (linked lists).        | Usually dynamic; nodes are connected via pointers or references.                |
| **Traversal**                   | Easy and simple; can traverse sequentially.                                 | More complex; may require recursion or specialized algorithms (e.g., BFS, DFS). |
| **Insertion/Deletion**          | Generally easier at ends (stacks, queues); middle operations may be costly. | Can be more complex; requires pointer adjustments and reorganization.           |
| **Relationship among elements** | Elements have a single predecessor and successor (except first and last).   | Elements can have multiple relationships.                                       |
| **Searching**                   | Linear search or binary search (if sorted).                                 | Searching is more complex; may require tree traversal or graph algorithms.      |
| **Examples**                    | Arrays, linked lists, stacks, queues                                        | Trees, Graphs                                                                   |
| **Use cases**                   | Simple data storage, sequential processing                                  | Representing hierarchical data, networks, relationships                         |
# Following Are The Data Structures:

## 1. Arrays
(The Foundation of Digital Storage)

An Array is a collection of items stored at **contiguous** (physically touching) memory locations. It is the simplest and most widely used data structure. The index maps directly to a memory address.

Computers love arrays. Why? Because of **CPU Caching**. When a processor reads an item from memory, it doesn't just grab that one tiny item; it grabs a "chunk" of memory around it. Since arrays are stored side-by-side, when you read index `0`, the computer automatically pre-loads index `1`, `2`, and `3` into the cache. This makes iterating over an array incredibly fast—faster than almost any other structure.

### Real Life Examples:
1. **Your Screen (The Framebuffer):**
   Every time you look at a monitor, you are looking at a massive 2D array. A 1920x1080 screen is just an array of roughly 2 million pixels. The graphics card updates this array 60 times a second (60Hz) to show you a video.
2. **Databases (Columnar Stores):**
   Modern analytics databases (like Snowflake or Amazon Redshift) store data in arrays by _column_ rather than row. This allows them to sum up "Sales_Total" for a billion rows in milliseconds because the data is contiguous in memory.
3. **Digital Audio (PCM Data):**
   A 3-minute MP3 song is actually a giant array of numbers (amplitude samples). CD quality audio is 44,100 array entries per second.
4. **Hardware & IoT Buffers:**
   When your keyboard sends a keystroke to the CPU, it goes into a tiny, fixed-size array called a "ring buffer." If you type too fast while the computer is frozen, you hear a "beep" because that array is full.
5. **Hash Tables (Under the hood):**
   Even complex structures like Hash Maps are built on top of arrays. Without arrays, almost nothing else would exist.

## 2. Linked Lists
(The Flexible Chains)

A linear data structure where elements are not stored in contiguous locations. Each element (called a **Node**) contains two things:
1. The Data.
2. A **Pointer** (or Reference) to the next node in the sequence.

Think of a Linked List like a **Scavenger Hunt**. You can't calculate where the 5th item is (like you can with an array). You _must_ go to the 1st item to find the address of the 2nd, then the 2nd to find the 3rd.
- **Singly Linked List:** One-way street (A -> B -> C).
- **Doubly Linked List:** Two-way street (A <-> B <-> C). You can go forward and backward.

### Real Life Examples:
1. **The Blockchain (Bitcoin/Ethereum):**
   The entire concept of crypto is a giant Linked List. Each "Block" contains data (transactions) and a "Hash Pointer" to the previous block. If you change one block, the link breaks, invalidating the whole chain.
2. **File Systems (FAT - File Allocation Table):**
   Old hard drives used linked lists to store files. If a file was too big for one spot, it stored the first chunk in one spot, which pointed to the next chunk physically located somewhere completely different on the disk.
3. **Music Playlist (Shuffle Mode):**
   When you create a playlist, the songs aren't copied into a new file. The software just creates a Doubly Linked List of pointers to your MP3 files. "Next" goes to the next pointer; "Prev" goes to the previous one.
4. **Alt-Tab (Windows Switching):**
   The list of open programs you cycle through is often a linked list. The most recently used app moves to the head of the list.
5. **Undo Functionality (Photoshop/Word):**
   Every action you take is a node added to the list. `Ctrl+Z` (Undo) moves the pointer back one step. `Ctrl+Y` (Redo) moves it forward.

## 3. Stacks
(The LIFO Specialist)

A linear structure that follows the **Last In, First Out (LIFO)** principle. The last item added is the _only_ one you can access.

Imagine a stack of cafeteria trays. You can only touch the top tray. If you want the bottom tray, you have to remove all the top ones first.

- **Push:** Add to the top.
- **Pop:** Remove from the top.
- **Peek:** Look at the top without removing.

### Real Life Examples:
1. **The "Call Stack" (Program Execution):**
   This is fundamental to how _all_ code runs. When Function A calls Function B, the computer "pushes" A onto a stack and runs B. When B finishes, it "pops" B off and resumes A. If you call too many functions (infinite recursion), you get the famous **Stack Overflow** error.
2. **Browser History:**
   - Site A -> Click Link to Site B -> Click Link to Site C.
   - Your history is a stack: [A, B, C].
   - Click "Back": Pop C. You are now at B.
   - Click "Back": Pop B. You are now at A.
3. **Syntax Parsing (Compilers):**
   How does VS Code know you missed a closing bracket `}`? It reads your code. When it sees `{`, it pushes it onto a stack. When it sees `}`, it pops the stack. If the stack isn't empty at the end of the file, it knows you forgot a closing bracket.
4. **Towers of Hanoi (Game Logic):**
   Many puzzle games rely on stack logic where items must be removed in reverse order of placement.
5. **Expression Evaluation:**
   Calculators use stacks to solve math like `3 + 4 * 5`. They push numbers and operators onto stacks to ensure multiplication happens before addition.

## 4. Queues
(The FIFIO Specialist)

A linear structure that follows the **First In, First Out (FIFO)** principle. It is open at both ends: data enters from the "Rear" (Enqueue) and leaves from the "Front" (Dequeue).

This is purely a **waiting line**. It ensures fairness. The longest-waiting item gets processed next.
- **Circular Queue:** A more efficient version where the end of the queue connects back to the start to save memory.

### Real Life Examples:
1. **CPU Task Scheduling:**
   Your computer runs hundreds of processes (Spotify, Chrome, System). The CPU uses a queue to give each process a tiny slice of time (2ms) in order.
2. **Web Server Request Handling (Node.js Event Loop):**
   Node.js (which you likely use) is famous for its "Event Loop." This loop is literally a Queue. Incoming API requests wait in the "Message Queue" to be processed one by one.
3. **Printer Spooler:**
   If everyone in the office hits "Print" at 9:00 AM, the printer doesn't panic. It puts every job in a queue and prints them strictly in arrival order.
4. **Keyboard Buffer:**
   If you type "HELLO" very fast, the letters enter a queue. The computer processes H, then E, then L... ensuring they appear on screen in the right order.
5. **Distributed Systems (Kafka/RabbitMQ):**
   In massive systems (like Netflix), "Message Queues" are used to decouple services. If the "Billing Service" is down, the "New User" requests aren't lost; they just sit in a queue until the billing service comes back online.

## 5. Hash Tables
(The Speed King)

A data structure that implements an "associative array" (Dictionary). It maps **Keys** to **Values**. It uses a mathematical formula (Hash Function) to calculate exactly where the data is stored in memory.

- **The Magic:** In an array, to find "John," you check index 0, then 1, then 2... (Slow). In a Hash Table, you take the string "John," run it through a math formula, and it spits out: `Index 492`. You go straight to index 492.
- **Complexity:** O(1) - Constant Time. This means finding a user in a database of 100 users takes the _same amount of time_ as finding a user in a database of 1 billion users.

### Real Life Examples:
1. **Passwords (Security):**
   Servers (usually) don't store your actual password. They store the _Hash_ of your password. When you log in, they hash your input and check if it matches the stored hash. This is why websites can't email you your forgotten password—they literally don't know it.
2. **Database Indexing:**
   When you run `SELECT * FROM Users WHERE email = 'test@gmail.com'`, the database uses a Hash Index (or B-Tree) to jump instantly to that row without scanning the whole table.
3. **Compilers (Variable Lookups):**
   When you run code and use a variable `count`, the computer looks up `count` in a symbol table (a hash map) to find its value.
4. **Caches (Browser & Server):**
   Your browser cache is a hash map. Key: `URL`, Value: `Image Data`. If you visit a site twice, it hashes the URL, sees the image is already in memory, and loads it instantly.
5. **Blockchain (Merkle Trees):**
   Cryptocurrencies use "Cryptographic Hashing" to verify that data hasn't been tampered with. If one bit changes, the hash changes completely.

## 6. Trees
(The Hierarchy)

A non-linear structure with a hierarchical relationship. Elements are nodes connected by edges.
- **Root:** The top node.
- **Parent/Child:** Direct relationship.
- **Leaf:** A node with no children.

Trees are optimized for searching and sorting huge datasets.
- **Binary Search Tree (BST):** A specific rule: Left child is smaller, Right child is bigger. This allows you to cut your search area in half with every step (O(log n)).

### Real Life Examples:
1. **The DOM (Document Object Model):**
   As a Full Stack Dev, you manipulate this daily. `<html>` is the root. `<body>` is a child. `<div>` is a child of body. When you do `document.getElementById`, you are traversing a tree.
2. **File Systems:**
   Your hard drive is a tree. `C:` is the root. `Program Files` is a branch. `LeagueOfLegends.exe` is a leaf node.
3. **Auto-Correct / Auto-Complete (Tries):**
   When you type "Alg...", Google suggests "Algorithms." It uses a **Prefix Tree (Trie)**. It travels down the branch A -> L -> G to see what words hang off that branch.
4. **Database B-Trees:**
   Almost all SQL databases use "B-Trees" for storage. They are wide, flat trees that allow databases to read millions of records with only tiny disk movements.
5. **Game AI (Decision Trees):**
   In games (like FIFA or Chess), the AI builds a tree of possible moves. "If I move here (Node A), player moves there (Node B)..." It searches the tree to pick the best path.

## 7. Graphs
(The Web of Connections)

A collection of nodes (Vertices) and edges that connect them.
- **Note:** A Tree is just a specific type of Graph (one with no loops). A Graph has no rules—everything can connect to everything.

Graphs represent relationships. They can be:
- **Directed:** A -> B (Twitter Follow: I follow you, but you don't follow me).
- **Undirected:** A - B (Facebook Friend: We are connected both ways).
- **Weighted:** The connection has a "cost" (e.g., distance between cities).

### Real Life Examples:
1. **Social Networks (The Social Graph):**
   Facebook is one massive graph. "People You May Know" algorithms analyze the graph: "You and John both share an edge with Sarah, so you should connect."
2. **GPS & Navigation (Google Maps):**
   Intersections are Nodes. Roads are Edges. The "Weight" of the edge is the traffic time. Dijkstra’s Algorithm runs on this graph to find the shortest path.
3. **The Internet Itself:**
   The web is a graph. Websites are nodes; Hyperlinks are edges. Google's "PageRank" algorithm works by seeing which nodes (sites) have the most incoming edges (links) from other important nodes.
4. **Package Managers (npm / pip):**
   When you `npm install react`, React relies on other packages, which rely on others. This is a **Dependency Graph**. npm must ensure there are no "Circular Dependencies" (A needs B, B needs A) or the install fails.
5. **Recommendation Engines (Netflix/Amazon):**
   "Users who bought A also bought B." This is a Bipartite Graph connecting Users to Products.