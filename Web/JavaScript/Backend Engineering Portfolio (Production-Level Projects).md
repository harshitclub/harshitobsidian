# 1. IdentityForge (Authentication & Authorization Service)

### What to build

A standalone authentication service designed to be reused across multiple systems.
### Features

- Signup, login, logout
- JWT + refresh token rotation
- Email verification and password reset
- Role-based access control (RBAC)
- Rate limiting on authentication endpoints
- Session management (optional using Redis)
### Concepts covered

- Authentication and authorization flows
- Security best practices
- Token lifecycle management
- Database schema design for auth systems
- Middleware architecture
### How to build it properly

- Implement refresh token rotation (avoid static tokens)
- Store tokens securely (database or Redis)
- Add brute-force protection and login throttling
- Use structured logging for auth attempts and failures
- Centralized error handling with custom error classes
- Validate all inputs using Zod
- Follow layered architecture (controller → service → repository)
- Dockerize service with database
### GitHub expectations

- Clear explanation of authentication flow
- Sequence diagram (login + refresh flow)
- Security decisions and trade-offs
- `.env.example` file
- API collection (Postman/Thunder Client)
---
# 2. QueryCraft (Advanced PostgreSQL API)

### What to build

A high-performance REST API for handling structured data (products, posts, users).
### Features

- Cursor-based pagination
- Filtering, sorting, and full-text search
- Index optimization
- Transactions and bulk operations
- Efficient query handling
### Concepts covered

- Query optimization
- Indexing strategies
- API design patterns
- Transaction management
### How to build it properly

- Use `EXPLAIN ANALYZE` and document performance
- Add query execution time logging
- Configure connection pooling
- Avoid N+1 query problems
- Optimize indexes based on query patterns
### GitHub expectations

- Before/after query optimization comparison
- Database schema diagram
- Indexing strategy explanation
- Performance benchmarking notes
---
# 3. MediaFlux (File Upload & Processing Service)

### What to build

A service responsible for uploading, storing, and processing media files.
### Features

- File upload (images/videos)
- Signed URL generation
- Image resizing and compression
- Metadata storage
- Background processing
### Concepts covered

- Streams and buffers
- File handling and I/O
- External storage integration
### How to build it properly

- Use streaming instead of loading files into memory
- Offload processing to background jobs (QueueForge)
- Validate file size and type strictly
- Log upload and processing lifecycle
- Handle failures gracefully
### GitHub expectations

- Architecture diagram for upload pipeline
- Storage strategy explanation
- File processing workflow documentation
---
# 4. CachePulse (Redis Caching System)

### What to build

A caching layer integrated with APIs to improve performance.
### Features

- Cache-aside pattern
- TTL-based expiration
- Cache invalidation strategies
- Hot key protection
### Concepts covered

- Performance optimization
- Caching strategies
- Data consistency trade-offs
### How to build it properly

- Track cache hit/miss ratio
- Handle stale data carefully
- Implement fallback mechanisms
- Avoid over-caching unnecessary data
### GitHub expectations

- Performance improvement metrics
- Cache strategy explanation
- Before/after latency comparison
---
# 5. QueueForge (Background Job Processing System)

### What to build

A distributed job processing system using BullMQ.
### Features

- Job queues (emails, media processing, etc.)
- Retry mechanism with exponential backoff
- Dead letter queue
- Worker processes
### Concepts covered

- Asynchronous processing
- Distributed systems basics
- Fault tolerance and retries
### How to build it properly

- Separate API service and worker services
- Log job lifecycle (queued → processing → success/failure)
- Ensure idempotent job execution
- Monitor queue performance
### GitHub expectations

- Job flow diagram
- Retry and failure handling strategy
- Worker architecture explanation
---
# 6. GateKeeper (API Gateway + Rate Limiter)

### What to build

A centralized API gateway that routes requests and protects services.
### Features

- Request routing
- Rate limiting (token bucket or sliding window)
- Authentication middleware
- Request logging and tracing
### Concepts covered

- API gateway architecture
- Rate limiting algorithms
- Distributed request handling
### How to build it properly

- Use Redis for distributed rate limiting
- Attach requestId to every request
- Log request metadata (latency, status, IP)
- Handle burst traffic efficiently
### GitHub expectations

- Rate limiting algorithm explanation
- Request flow architecture diagram
- Test scenarios (load, burst traffic)
---
# 7. LinkLite (Scalable URL Shortener)

### What to build

A high-read optimized URL shortener system.
### Features

- Short URL generation
- Fast redirection
- Click analytics
- Redis caching
### Concepts covered

- High-read system design
- Database indexing
- Caching strategies
### How to build it properly

- Cache frequently accessed URLs in Redis
- Optimize DB lookups using indexes
- Handle key collisions
- Log redirect latency and usage
### GitHub expectations

- Scaling strategy explanation
- Read optimization techniques
- Caching logic documentation
---
# 8. CommerceCore (E-commerce Backend System)

### What to build

A modular and scalable backend system simulating an e-commerce platform.
### Features

- Product service
- Order service
- Inventory management
- Payment simulation
- Event-driven updates using queues
### Concepts covered

- Complex workflows
- Transactions and consistency
- Event-driven architecture
### How to build it properly

- Use queues for order processing
- Handle failure scenarios (payment failure, stock issues)
- Maintain data consistency across services
- Log complete order lifecycle
### GitHub expectations

- System architecture diagram
- Event flow documentation
- Data consistency strategy
- Failure handling explanation

---
# 9. ObservaStack (Monitoring & Observability Platform)

### What to build

A centralized observability system integrated with your backend services.
### Core stack

- Metrics: Prometheus
- Visualization: Grafana
- Logging: Loki
- Tracing: Jaeger
### Features

#### Metrics Collection

- Request count
- Response time (latency)
- Error rate
- CPU and memory usage
- Queue length
#### Dashboards

- API performance
- Database query time
- Cache hit/miss ratio
- Queue processing stats
#### Centralized Logging

- Aggregate logs from all services
- Search using requestId
- Correlate logs with errors
#### Distributed Tracing

- Track requests across services
- Example: Gateway → Auth → Order → Queue
#### Alerts

- High error rate
- Slow response times
- Queue backlog
- Resource spikes
---
# Project Standards (Apply to ALL Projects)

---
## Folder Structure

```
src/  modules/  controllers/  services/  repositories/  middlewares/  utils/  config/
```
---
## Logging

- Use structured logging (Pino or Winston)
- Include requestId, userId, timestamp
- Log errors, important flows, and performance
---
## Error Handling

- Custom error classes
- Centralized error middleware
- Do not expose internal errors
---
## Docker

- Use docker-compose for every project
- Include:
    - application service
    - database
    - Redis (if required)
---
## Validation

- Validate all inputs using Zod
- Never trust raw request data
---
## README (Critical for Portfolio)

Each project must include:

- Problem statement
- Architecture diagram
- Tech stack
- Setup instructions
- Key decisions and trade-offs
- Scaling considerations
---
## Additional Signals

- API collection (Postman/Thunder Client)
- `.env.example`
- Seed scripts
- Basic tests
---
## Show Engineering Thinking

Explain clearly:

- Why specific technologies were chosen
- How system behaves under load
- Failure scenarios and handling
- Trade-offs made