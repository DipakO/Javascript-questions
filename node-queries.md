# Node.js

## 1. What is Node.js?
**Answer:**
Node.js is a JavaScript runtime built on Google's V8 JavaScript engine. It allows us to execute JavaScript outside the browser, mainly for backed and server-side applications.
Node.js uses an event-driven, non-blocing I/O model. This makes it suitable for applications that handle many concurrent I/O operations such as API's, database calls, file operations, and network requests.
Internally, JavaScript execution is handled by the V8 engline, while Node provides additional capabilities such as networking, filesystem access, HTTP, streams, and process management.

**Cross-question**

### 1) Is Node.js a programming language?
**Answer:** No. JavaScript is the programming language. Node.js is a runtime environment that allows JavaScript to run outside the browser.

### 2) Is Node.js a framework?
**Answer:** No. Node.js is a runtime. Frameworks such as Express.js and NestJS run on top of Node.js.

### 3) Why is Node.js popular for backend development?
**Answer:** 
JavaScript/TypeScript can be used across frontend and backend
Not-blocking I/O
Good for I/O-heavy applications
Large npm ecosystem
Easy API development
Good support for real-time applications
Easy horizontal scaling

### 4) Is Node.js good for every backend application?
**Answer:** No. Node.js is particularly strong for I/O-bound workloads. For CPU-heavy workloads such as intensive image processing, large computations, or complex data processing, running the work directly on the main JavaScript thread can block the event loop. In those cases, worked threads, backgo=round jobs, separate services, or another runtime may be more appropriate.

## 2. How does Node.js handle multiple request if JavaScript is single-threaded?
**Answer:** JavaScript execution in Node.js is primarily single-threaded, meaning the JavaScript code runs on a main thread. However, Node.js can handle many concurrent requests because it uses an event-driven, non-blocking I/O architecture.
When Node encounters an asynchronous operation such as a database call, filesystem operation, or network request, it doesn't block the JavaScript thread waiting for the operation to finish. The operation is handled asynchronously, and once it completes, its callback or continuation is scheduled to run.
This allows the main thread to continue processing other requests instead of waiting.

Simplifies: 

```ts
Request A => Node starts DB operation => Doesn't wait => Request B => Request C => DB operation A completes => Callback/Promsie continuation runs 
```

**Cross-question**

### 1) But isn't Node.js single-threaded?
**Answer:** 
The JavaScript execution model is primarily single-threaded, but Node itself can use other threads internally through mechanisms such as the libuv thread pool and worker threads.

## 3. What os the Event loop?
**Answer:** 
    The event loop is the mechanism that allows Node.js to perform non-bloacking asychrouns operations while javascript executes on a single main thread.
    Instead of waiting for asynchronous operations to complete, Node registers the operation and continues executing other javascript. When the asynchronous operation is ready, the event loop coordinates when its callback or continuation can execute.

Flow:
```ts
JavaScript => Call Stack => Async operation => Node / OS / libuv => Operation completes => Queue => Event loop => Call Stack
```

**Cross-question**

### 1) What happens if we can CPU-heavy code?
**Answer:**
```ts
function heavyTask() {
    for (let i = 0; i < 10_000_000_000; i++) {
        // heavy computation
    }
}
```

The javascript thread becomes busy executing that function. While it is running, the event loop cannot process other JavaScrpit callbacks normally. Therefore, incoming request can become delayed.

This is called **event-loop blocking.**

## 4. What is blocking vs non-blocking code?
**Answer:** 
**Blocking**
```ts
const data = fs.readFileSync("file.txt");
```

The execution waits until the file is read.

**Non-blocking**
```ts
const data = await fs.promises.readFile("file.tsxt");
```

The operation is asynchronous, allowing Node to handle other work while waiting.

Blocking code prevents the current JavaScript execution thread from continuing until the operation completes. Non-blocking code starts an asynchronous operation and allows the event loop to continue processing other work.

**Cross-question**

### 1) Does await block Node.js?
**Answer:**
    await pauses the execution of the current async function, but it
does not block the Node.js event loop while waiting for the Promise to settle.

Exm.
```ts
async function getUser() {
    const user = await getUserFromDatabase();

    return user;
}
```
The function pauses at await, but Node can process other requests while the database operation is pending.

## 5. What is libuv?
**Answer:**
    libuv is a C library used by Node.js that provides the underlying
event-driven asynchronous I/O capabilities.
It helps Node.js handle asynchronous operations such as networking and filesystem operations and also provides the event loop and a thread pool for certain operations.

**Cross-question**

### 1) Does Node.js itself implement the event loop?
**Answer:** 
    Node.js exposes the event-driven programming model, but the
underlying event loop implementation is largely provided through libuv.

## 6. What is the libuv thread pool?
**Answer:**
    Node.js has a thread pool used for certain operations that cannot be handled purely through non-blocking OS APIs.

By default, the thread pool has: 
```ts
4 threads
```

It can be configured using:
```ts
UV_THREADPOOL_SIZE
```

The libuv thread pool allows Node.js to offload certain potentially blocking p=operations so that they don't block the main JavaScript thread.

Examples can include: 
- filesystem operations
- some DNS operations
- cryptographic operations
- compression-related operations

**Cross-question**

### 1) Does every async operation use thread pool?
**Answer:**
No. For eg. many network operations are handled using the operating system's asynchronous networking capabilities rather than consuming a libuv thread-pool thread.

## 7. Explain the difference between concurrency and parallelism.
**Answer:**

**Concurrency**
Multiple tasks are in progress during overlapping periods.

**Parallelism**
Multiple tasks are literally executing at the same time.

**Node.js**

The main JavaScript execution is generally single-threaded, so javascript execution isn't automatically parallel.

But Node can achieve parallel work using:
- worker threads
- multiple Node processes
- cluster/process managers
- external services

Node.js provides concurrency primarily through its event-driven asynchronous model. For actual CPU parallelism, we can use worker threads or multiple processes.

## 8. How do you handle errors with async/await?
Normal approach
```ts
try {
    const user = await getUser();
} catch (error) {
    console.error(error);
}
```

I normally handle expected operation failures at the appropriate service or controller boundary and use centralized error handling for HTTP responses. I avoid putting unrelated error handling into every function if the application already has centralized error handling.

## 9. What is process.nextTick()?
**Answer:**
```ts
process.nextTick(() => {
    console.log("next tick");
});
```
process.nextTick() schedules a callback to run after the current operation completes, before the event loop continues to later phases.

process.nextTick() has very high priority/
Excessive recursive use can prevent the event loop from progressing.

## 10. What are microtasks?
**Answer:**
Promisses use the microtask queue.

```ts
Promise.resolve().then(() => {
    console.log("promise");
});
```
The callback is schedules as a microtask.

IMP Node concepts:

```ts
process.nextTick()
Promise microtasks
Event loop phases
```

## 11. What are Node.js streams?
**Answer:**

Streams allow us to process data increamentally instead of loading the entire data set into memory at once.

Types: 
```ts
Readable
Writable
Duplex
Transform
```

```ts
const stream = fs.createReadStream("large-file.txt");

stream.on("data", chunk => {
    console.log(chunk);
});
```
instead of:
```ts
const file = fs.readFileSync("huge-file.txt");
```

which may load the whole file into memory.

**Cross-question**

### 1) Where are streams useful?
**Answer:**
- large files
- video/audio
- HTTP requests/responses
- file uploads/donwloads
- data processing pipelines

## 12. What is backpressure?

Imagine: 

Procuder => Consumer

Producer generates:

100 MB/sec

Consumer processes:

10 MB/sec

Data starts accumulating.
That's backpressure.

Backpressure occurs when the producer generates data faster than the consumer can process it. Streams provide mechanisms to control the flow so that memory usage doesn't grow uncontrollably.

This matters heavily with:
- file uploads
- large downloads
- streaming APIs
- data processing

## 13. CommonJS vs ES Modules

**CommonJS**
```ts
const express = require("express");

module.exports = router;
```

**ES Modules**
```ts
import express from "express";

export default router;
```

CommonJS is Node's older module system, while ES Modules are the standardized JavaScript module system using import and export. Modern Node.js supports both depending on project configuration.

**Cross-question**

### 1) Why does this matter?

Because module configuration affects:
- imports 
- exports
- package configuration
- TypeScript compilation
- interoperability
- runtime behaviour

## 14. What is package.json ?

package.json describes a Node.js project's metadata, dependencies, scripts, package configuration, and other project settings.

**Cross-question**

### 1) dependencies vs devDependencies?

dependencies: 
Packages required by the application at runtime.

devDependencies
Packages primarily required during development/build/test processes.

Exm;

express => dependency
typescript => devDependency
esling => devdependency

## 15. What is package-lock.json?

package-lock.json locks the exact dependency tree resolved during installation, including transitive dependencies. This helps different environments install consistent versions.

**Cross-question**

### 1) Why not just use: 'express': "^5.0.0"?

Because ^ allows compatible version updates.
The lock file records the actual resolved versions.

## 16. What is middleware in Node/Express?

Middleware is a function that runs during the request-response lifecycle. It can inspect or odify the request and response, perform authentication or validation, log requests, and either end the response or pass control to the next middleware.

Exm: 
```ts 
app.use((req, res, next) => {
    console.log(req.method, req.url);

    next();
});
```
Flow: 
Request => Middleware 1 => Middleware 2 => Controller => Response

## 17. What is the difference between middleware, controller, and service?

**Middleware**
Deals with request lifecycle concerns.

Exm
logging
request preprocessing
basic request context

**Controller**
Deals with HTTP layer.

GET /users
POST /users

**Service**
Contains appication/business logic.

Good architecture

Request => Middleware => Guard/Auth => Controller => Service / Use case => Repository => Database

NestJS will formalize much of this architecture.

## 18. How do you handle errors in a Node.js backend?

I prefer centralized error handling rather than handling every error independently at the controller level. Business or service layers can throw meaningful application errors, and the HTTP layer can translate those errors into appropriate HTTP responses.
I also distinguish expected application errors from unexpected system errors and make sure unexprected errors are logged with enough context for debugging without exposing sensitive infroamtion to clients.

## 19. What happens if middleware doens't call next()?

```ts
app.use((req, res, next) => {
    console.log("Hello");
});
```

If it doens't send a response and doesn't call next():
The request can remain hanging because Express has no instruction to continue to the next middleware or finish the response.

## 20. What is the difference between operational and programming errors?

**Operational error**

Expected runtime failure:

Database unavailable
Invalid input
Network timeout
File not found
Unauthorized request

**Programmin error**

Bug in code:
```ts
const user = undefined;

user.name;
```
Operational errors are failures that can occur during normal system operation and can often be handled or reported appropriately. Programming erros usually indicate a bug that should be fixed in the code. I don't treat every error the same way.

## 21. How would you improve Node.js API performance?

I'd look at:

**1. Database**
Indexes
Query optimization
Projection
Pagination
Avoid unnecessary queries

**2. Application**
Avoid event-loop blocking
Parallelize independent asynch operations
Reduce unnecessary processing
Use streams for large data.

**3. Caching**
Redis
Application cache
HTTP caching

**4. Architecture**
Horizontal scaling
Load balancing
Background jobs
Queues

**5. Observability**
Latency
Error rate
Throughput
CPU
Memory
Database latency

I wouldn't optimize Node.js in isolation. I'd first identify where the latency is coming from using metrics and tracing, then optimize the bottleneck. Depending on the bottleneck, that could mean database indexes, reducing calls, parallelizing independent oprations, caching, preventing event-loop blocking, or moving expensive work to background workers.

## 22. What causes memory leaks in Node.js?

Possible causes:
- Global variables holding references
- Long-lived caches without eviction
- Event listeners not removed
- Timers remaining large objects
- Closures retaining large objects
- Unbounded arrays/maps
- Improper resource cleanup

Exm.
```ts
const cache = new Map();

function addData(data) {
    cache.set(data.id, data);
}
```

If entries are never removed:

Map grows => Memory grows => Envetually memory pressure

**Cross question**

### 1) How would you investigate a memory leak?

I'd first monitor usage over time. If memory continuously grows without returning to a stable baseline, I'd take keep snapshots and compare them to identify objects that remain retianed unexpectedly. I'd then inspect references, caches, listerners, timers, and other long-lived objects.

## 23. What is process.env?

Environment variables are commonnly used for configuration:
```ts
const port = process.env.PORT;
```

Exm: 
DATABASE_URL
JWT_SECRET
PORT
NODE_ENV

**Cross question**

### 1) Should secrets be hardcoded ?

```ts
const password = "my-secret-passowrd"
```

No. Secrets should be managed through environment/configuration or a dedicated secrets manager, depending on the deployment environment.

## 24. What is NODE_ENV?

Common values:

development
production
test

It can be used to change env-specific behavior.

## 25. How would you scale a Node.js application?

Suppose: 1 Node process isn't enough. 

You can run multiple instances:

             Load Balancer
             /     |     \
            /      |      \
        Node 1   Node 2   Node 3

Node.js applications can be scaled horizontally by runnig multiple application instances behind a load balancer. The application should ideally remain stateless so requests can be handeled by nay instance. Shared state such as sessions or caching can be stored in external systems such as Redis or a database.

**Cross question**

### 1) Why stateless?

Suppose user logs into: Node 1
Then next request goes to: Node 2

If session data exists only in Node 1 memory, Node 2 won't know about it.

So we use: 
Redis
Database
JWT
External session store

## 26. What is graceful shutdown?

Imagine your server receives: STGTERM

during deployment.
You don't want to immediately kill it while requests are processing.

Graceful shutdown means allowing the application to stop accepting new work while giving existing requests and resources enough time to finish cleanly.

Typical cleanup: 

Stop accepting requests
        ↓
Finish active requests
        ↓
Close database connections
        ↓
Close message queue connections
        ↓
Close server
        ↓
Exit

## 27. How would you desing a production Node.js API?

Client
  ↓
Load Balancer
  ↓
Node/NestJS instances
  ↓
Authentication
  ↓
Controller
  ↓
Service / Use Case
  ↓
Repository
  ↓
MongoDB

       ↘ Redis
       ↘ Queue
       ↘ External APIs

With:
Logging
Monitoring
Tracing
Error handling
Validation
Rate Limiting
Authentication
Authorization

And deployment:
CI/CD
 ↓
Build
 ↓
Tests
 ↓
Deploy
 ↓
Multiple instances

## 28. Senior Scenario: Your Node API suddenly becomes slow. What do you check?

**Step 1 -- Check metrics**
Request latency
Error rate
Throughput
CPU
Memory

**Step 2 -- Check event loop**
Is CPU-heavy work blocking the event loop?

**Step 3 -- Database**
Slow queries
Missing indexes
Connection pool
Locks/contention

**Step 4 -- External services**
API latency
Timeouts
Retries

**Step 5 -- Application**
Sequential awaits
Large payload processing
Memory pressure
Serialization

**Step 6 -- Infrastructure**
Load balancer
Network
Container resources
Scaling

I would first identify whether the latency is coming from the application, database, external dependencies, or infrastructure rather than assuming Node itself is the problem. I'd use metrics, logs, and tracing to isolate the bottleneck and then optimize the specific component.

## 29. Seniour scenario: Your API receives 10000 requests at the same time. What happens?

Node doesn't create one JavaScript thread per request. Requests are handled throgh the event-driven model. If the requests are mostly I/O-bound, Node can keep many of them in flight concurrently. However, the system can still become contrained by CPU, memory, database connections, downstream services, network capacity, or rate limits.

## 30. Your endpoint performs heavy image processing. Should you do it directly in the request?

HTTP request => Create Job => Queue => Worker => Image processing => Store result

Then:
Client => GET /job/:id

or use WebScoket/events depending on requirements.

For expensive CPU-bound work, I would avoid performing the work directly on the main request thread. i'd consider worker threads or, for larger workloads, a background job/queue architecture so API instances remain responsive.

**Cross question**

### 1) Why Node.js?

Why Node?
↓
Is Node single-threaded?
↓
How does it handle concurrent requests?
↓
Explain event loop.
↓
What is libuv?
↓
What is thread pool?
↓
Does every async operation use thread pool?
↓
What happens with CPU-heavy work?
↓
How do you solve it?
↓
How would you scale Node?
↓
How do you monitor performance?