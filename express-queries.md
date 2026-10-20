# Express.js

## 1. What is Express.js?

Express.js is a lightweight web framework built on top of Node.js. It provides features for building HTTP servers and APIs, such as routing, middleware, request/response handling, and error handling

Without Express, Node can create an HTTP server directly:
```ts
import http from "http";

const server = http.createServer((req, res) => {
    res.end("Hello");
});
```

With Express:
```ts
import express from "express";

const app = express();

app.get("/", (req, res) => {
    res.json({ message: "Hello" });
});

app.listen(3000);
```
Express makes HTTP application development much easier.

**Cross question**

### 1) Is Express a replacement for Node.js?

No.
Express is not a replacement for Node.js. Node.js is the runtime environment, while Express is a framework that runs on top of Node.js and provides abstractions for handling HTTP applications.

### 2) Why use Express instead of Node's HTTP module?

Node's HTTP module is sufficient for creating a server, but as the application grows, handling routing, middleware, request parsing, error handling, and other common concerns manually becomses cumbersome. Express provides these capabilities in a simpler and more organized way.

### 3) Is Express opinionated?

Express is relatively unopinionated. It gives us core capabilities like routing and middleware but doesn't force a specific project structure, database, or business architecture. This provides flexibility, but it also means the development team needs to establish its own architecture and conventions.



## 2. What does Express actually provide?

Express mainly provides abstractions around HTTP application developemtn. Its core features include routing, middleware, request and response handling, and error handling. It also allows us to organize routes using routers and extend the application through middleware and third-party packages.

The important pieces are:
Routing
Middleware
Request handling
Response handling
Error handling
Router organization

For eg. 
```ts
app.get("/users", controller);
```

Express handles matching the incoming request to the route.

**Cross question**

### 1) Does Express provide databse functionality?

No. Express doesn't provide database functionality itself. We use seprate database drivers or libraries such as Mongosse for MongoDB, Prisma for supported databases, or native database clients.

### 2) Does Express provide authentication?

Not directly. Authentication is normally implemented through middleware and external libraries or application-specific logic. Express provides the request pipeline where authentication can be intergated.

### 3) Why is Express called minimal?

Because Express provides the fundamental HTTP building blocks without forcing a complete application architecture. Features such as validation, authentication, database access, and dependency injection are generally added separately.

## 3. Explain the Express request-response lifecycle

When a request reaches an Express application, it passes through the middleware and routing pipeline in the order in which they were registered. Middleware can inspect or modify the request, perform tasks such as authentication or logging, and either pass control to the next middleware or send a response. Eventually a matching route handler processes the reuest and sends the response. If an error occurs, it can be passsed to error-handling middleware.

Suppose we have:
```ts
app.use(logger);

app.use(auth);

app.get("/users", getUsers);

app.use(errorHandler);
```

The flow is:
HTTP request => logger => auth => route matching => getUsers => HTTP Response

If something fails:
HTTP Request => logger => auth => getUsers => Error => errorHandler => HTTP Response

The order in which middleware is registered mattters.

**Cross question**

### 1) Does middleware order matter?
Yes, Express processes middleware and routes in registration order. Therefore, middleware that needs to run before a route must be registered before that route.

### 2) What happens if no route matches?
If no route or middleware handles the request, the request can eventually reach a 404 handler if the application defines one. Otherwise Express will produce its default not-found behavior.

### 3) Where should authentication happen?
Authentication should happens before the protected controller executes. Depending on the application, it can be applied globally, to a router or to individual routes.

## 4. What is middleware?

Middleware is a function that has access to the request, response and the next middleware in the request pipeline. It can perform processing, modify the request or response, terminate the request, or pass control to the next middleware.

```ts
app.use((req, res, next) => {
    console.log(req.method, req.url);

    next();
});
```

**Cross question**

### 1) What are common type of middleware?
Common categories include application-level middleware, router-level middleware, built-in middleware, third-party middleware, and error-handling middleware.

### 2) Can middleware modify req?
Yes, Middleware can attach additional information to the request object. A common example is authentication middleware attaching the authenticated user's information so later handlers can access it.

### 3) Should business logic be inside middleware?
Generally no. Middleware should focus on cross-cutting request concerns such as authentication, logging, or validation. Business logic should normally be places in a service or use-case layer.

## 5. Can middleware send the response itself?

Yes. Middleware can terminate the request by sending a response. This is commonly used when a request should not continue, for example when authenication fails or validation fails. In that case we don't call next()

```ts
app.use((req, res, next) => {
    if (!req.headers.authorization) {
        return res.status(401).json({
            message: "Unauthorized"
        });
    }

    next();
})
```

**Cross question**

### 1) Why use return?
The return prevents the fucntion from continuing after the response has been sent. Without it, additional code could execute and potentially attempt to send another response.

### 2) What happens if we call next() after sending a response?
It can cause the request to continue even though we've already attempted to finish it, which can lead to unexpected behaviour or errors such as 'headers already sent.'

## 6. What is the difference between app.use() and app.get()?
app.use() is priamarily used to register middleware or mount routers, while
app.get() defines a route handler specifically for HTTP GET request. app.use() can also apply middleware to a path prefix, whereas app.get() matches a specific HTTP method.

aap.use()
Generally used for middleware or mounting routers.

```ts
app.use(logger);
```

or
```ts
app.use("/api/users", userRouter);
```

app.get()
Defines a route specifically for HTTP GET requests.

```ts
app.get("/users", getUsers);
```

Similarly:

```ts
app.post()
app.put()
app.patch()
app.delete()
```

## 7. What is an Express Router?
An Express Router is a modular routing system that allows us to group related rotes into separate modules. Instead of defining every route in the main application file, we can organize routes by feature or resource and mount them under a common path.

instead:

src/
├── app.ts
├── routes/
│   ├── user.routes.ts
│   └── order.routes.ts

Example:

```ts
// user.routes.ts

import { Router } from "express";

const router = Router();

router.get("/", getUsers);
router.get("/:id", getUser);
router.post("/", createUser);

export default router;
```
Then:

```ts
// app.ts

app.use('/api/users', userRouter);
```

Now:
GET /api/users
GET /api/users/:id
POST /api/users

**Cross question**

### 1) Why use Router?

It improves oraganization and separation of concerns. In a larger application, we can keep user routes, order routes, authentication routes, and other features separate instead of having a single large application file.

### 2) Can middleware be applied to a router?

Ys.

### 3) Router-level vs application-level middleware?

Application level middleware can affect the whole application or a broad path, while router-level middleware applies only to routes belonging to a particular router.

## 8. What are route parameters?
Route parameters are dynamic values embedded in the URL path. Express makes them available through req.params. They're commonly used when identifying a specific resource, such as a user ID.

Exm: 
```ts
app.get("/users/:id", (req, res) => {
    console.log(req.params.id);
});
```
Request: GET /users/123

Then: 
```ts
req.params.id
```

is: 123

**Cross question**

### 1) When would you use params instead of query params?

I generally use route parameters to identify a specific resource and query parameters for optional filtering, sorting, pagination, or other request options.

## 9. req.params vs req.query vs req.body
req.params contains values captured from dynamic URL segments, req.query contains query-string parameters, and req.body contains data sent in the request body. I choose between them based on the purpose of the data; params usually identify resources, query parameters modify or filter a request, and the body usually contains the payload for operations such as creating or updating data.

**req.params**
Values embedded in the URl path.

/uses/123

```ts
req.params.id
```

**req.query**
Values after ?.

/users?page=2&limit=10

```ts
req.query.page
req.query.limit
```

**req.body**
Data sent in the request body.

```json
{
    "name": "John",
    "email": "john@example.com"
}
```

Access:
```ts
req.body.name
```

**Cross question**

### 1) Should sensitive data be sent in query parameters?

Generally, sensitive data such as passwords or authentication secrets should not be placed in query parameters because URLs can be logged, cached, stored in brower history, or appear in monitoring systems. Appropriate secure mechanisms should be used instead.

## 10. What does express.json() do?
express.json() is built-in Express middleware that parses incoming requests containing JSON payloads and makes the parsed data available through req.body. It only handles parsing; it does not validate whether the payload has the correct structure or bussiness values.

**Cross question**

### 1) Does it validate the body?

No, It only parses JSON. validation must be handled separately using a validation library or custom validation logic.

### 2) Why configure a body-size limit?

To prevent unnecessarily large payloads from consuming excessive server resources and to reduce the risk of abuse.

If the client sends JSON

```json
{
    "name": "john"
}
```

Express needs JSON body parsing middleware.

```ts
app.use(express.json());
```

Then:

```ts
req.body
```
contains the parsed JavaScript object.

Without appropriate body parsing:

```ts
req.body
```

may not contain the parsed JSON payload.

## 11. What is the JSON body size limit?
The JSON body-sixe limit defines the maximum payload size that Express's JSON parser will process. It's useful for protecting the application from unexpectedly large requests and controlling resource consumption. The exact limit should depend on the application's requirements rather than blindly using one value everywhere.

You can configure it:
```ts
app.use(
    express.json({
        limit: "1mb"
    })
);
```

This means Express won't accept JSON bodies larger than approx 1 MB through that parser.

**Why is this useful?**

It protects the application from unnecessarily large payloads.

**Cross question**

### 1) What happens if the payload exceeds the limit?

The JSON parser rejects the request before the controller processes it, and the application can handle that parsing error through its error-handling mechanism.

### 2) Would this limit protect file uploads?

Not necessarily. express.json() specifically handles JSON bodies. File uploads normally use multipart/form-data and require appropriate multipart handling and separate size limits.

## 12. Does express.json() validate the request?
No. parsing and validation are two different responsibilities. express.json() converts the JSON payload into a JavaScript object. It doesn't verify required fields, data types, business rules, or whether unexpected fields are allowed.

```json
{
    "age": "hello"
}
```

Can still be parsed as valid JSON.
But application may reject it because:
age must be a number

**Cross question**

### 1) What can we use for validation?
Depending on the project, we can use libraries such as Zod, Joi, express-validator, or class-validator, or implement custom validation where appropriate.

## 13. What is error-handling middleware?
Error-handling middleware is a special type of Express middleware used to centrally process errors that occur during request handling. Express identifies it by its four argument signature: error, request, response, and next. This allows us to keep error response logic in one place instead of duplicating it across every controller.

```ts
app.use((err, req, res, next) => {
    console.error(err);

    res.status(500).json({
        message: "Internal server error"
    });
});
```

**Cross question**

### 1) How does Express know this is error middleware?

Express identifies error-handling middleware by its four paramenters: err, rew, res, and next.

### 2) How do we send an error to it?
```ts
next(error);
```

### 3) Should every error return 500?

No. Known application errors should return appropriate status codes. For example, invalid input might be 400, authentication failure 401, authorization failure 403, resource not found 404, and a conflict such as a duplicate unique resource might be 409. Unexpected errors generally result in 500.

## 14. Why should error middleware usually be registered last?
Express processes middleware in registration order. Error-handling middleware is generally placed after the routes and other middleware so that errors genrated earlier in the request pipeline can propagate to it.

```ts
app.use(express.json());

app.use('/ap/users', userRouter);

app.use(errorHandler);
```

**Cross question**

### 1) Can error middleware be placed earlier?

It can be registered earlier, but it won't automatically handle errors from middleware or routes that are registered after it in the normal pipeline. Therefore, the centralized error handler is conentionally placed near the end.

## 15. How do you pass an error to the error handler?
In Express, middleware or route handlers can call next() with an error object. Express recognizes that as an error and skips normal middleware until it reaches an error handling middleware.

```ts
try {
    const users = await userService.getUsers();
    res.json(users);
} catch (error) {
    next(error);
}
```

**Cross question**

### 1) What happens after next(error)?

Express switches from the normal middleware pipeline to the error-handling pipeline and looks for error-handling middleware.

## 16. How do you handle async errors?
For asynchronous route handlers, errors from rejected promises need to react the Express error-handling mechanism. Depending on the Express version and project setup, this can be handled through native async error propagation or by explicitly wrapping handlers and forwarding rejected promises with next(). The important point is that asynchronous failures should reach centralized error handling rather than becoming unhandled prmoise rejections.

```ts
const asyncHandler = (handler) => (req, res, next) => {
    Promise.resolve(handler(req, res, next)).catch(next);
};
```
**Cross question**

### 1) Why use an async wrapper?

It avoids repeating the same try-catch and next(error) pattern in every asynchronous route handler.

### 2) Should we catch every error in every function?

Not necessarily. Lower-level functions can throw meaningful errors, while the HTTP layer can centrally translate those errors into HTTP responses. The exact boundary depends on the architecture.

## 17. What is middleware order?
Middleware order is the sequence in which Express ececutes registered middleware and routes. Since Express processes them in order, the position of middleware must execute before a protected controller, and error-handling middleware should generally be registered after the routes it needs to handle.

Example: 
```ts
app.use(auth);

app.get("/users", getUser);
```

Authentication runs first.

**Cross question**

### 1) What if we register the route first?

```ts
app.get("/users", getUsers);

app.use(auth);
```

The route can handle the request before the later middleware gets a chance to process it. Therefore, the authentication middleware would not protect that route in the intended way.

### 2) Why does order matter for:
express.json()
auth
validation
routes
errorHandler

Each stage depends on the previous stage. For example, body parsing need to happen before body validation, authentication needs to happen before authorizatioon or protected controller logic, and the error handler needs to be available after errors are generated.

## 18. How would you implement authentication middleware?
Authentication middleware verifies the client's credentials, such as a JWT or session. If the credentials are valid, it can attach the authenticated user's identity or claims to the requested and call next(). If authentication fails, it should terminate the request with an appropriate response, usually 401.

```ts
const authMiddleware = async (req, res, next) => {
    const token = req.headers.authorization;

    if (!token) {
        return res.status(401).json({
            message: "Unauthorized"
        });
    }

    // verify token

    req.user = user;

    next();
};
```
**Cross question**

### 1.  Where should token verification happen?

It can happen inside authentication middleware or a dedicated authentication service/helper. I prefer keeping the middleware responsible for the HTTP/request concern and delegaring token verification logic to a reusable component when the application grows.

### 2. Should authentication and authorization be the same middleware?

They can be combined in simple applications, but conceptually they are different responsibilities. Authentication establishes who the user is, while authorization determines whether that user has permission to perform a particular action.

## 19. Authentication vs Authorization
Authentication answers 'Who are you?' while authorization answers 'What are you allowed to do?'. For rxample, validating a JWT authenticates the user, while checking whether the user's role allows them to delete another user is authorization.

Example: 
Authentication
      ↓
User = Anoop

Authorization
      ↓
Role = USER
      ↓
DELETE /users/123
      ↓
Not allowed

**Cross question**

### 1) Can an authenticated user receive 403?

Yes. A user can be successfully authenticated but still not have permission to access a resource. In that case, 403 is appropriate.

## 20. What is the difference between 401 and 403?
401 means the result does not have valid authentication credentials, while 403 means the server understands who the requester is but that requester is not permitted to perform the requested operation.

Simple: 

401 => Who are you?
403 => You're identified, but you're not allowed.

**Cross question**

### 1) What if the JWT is expired?

The authentication credentials are no longer valid, so the request should generally be treated as unauthernticated and return 401.

### 2) What if the user is authenticated but isn't an admin?

If the endpoint requires admin permissions, the user can be authenticated successfully but should receive 403 because they don't gave sufficient authorization.

## 21. How would you strucutre an Express application?
For a small application, a simple route-controller-service structure can be sufficient. As the application grows, I prefer separating responsibilities such as configuration, routes, controllers, services or use cases, repositories, validation, middleware, models, and error handling. The exact structure should reflect the application's complexity rather than adding folders only for the sake of architecture.

Example: 

src/
├── config/
├── controllers/
├── routes/
├── services/
├── repositories/
├── middleware/
├── validators/
├── models/
├── errors/
├── utils/
├── app.ts
└── server.ts

**Cross question**

### 1. Why separate controller and service?

The controller is responsible for HTTP concerns such as reading request data and creating the response. The service handles application or business logic. Separating them makes the business logic easier to reuse and test without depending directly on Express.

### 2. Why separate repository and service?

The repository handles persistence and databse interaction, while the service handles application logic. This separation reduce couling between business logic and the database implementation.

## 22. Should business logic be placed inside controllers?
Generally, I avoid putting significant business logic inside controllers. Controllers should mainly coordinate the HTTP request and response. Business rules should be handled by services or use cases so they can be reused, tested, and maintained independentrly or Express.

Controller => Service / Use Case => Repository => Database

**Cross question**

### 1. Is a service always required?

No. For a very small endpoint, adding multiple abstraction layers can create unnecessary complexity. The separation becomes more valuable as business logic and application complexity increase.

## 23. What is app.use("/api", router)?
app.use() can mount an Express Router under a specific path prefix. This allows us to define routes inside the router using shorter paths while exposing them under a common API prefix.

```ts
app.use("/api/users", userRouter);
```

Router:
```ts
router.get('/');
router.get('/:id');
```

Final routes: 

GET /api/users
GET /api/users/:id

**Cross question**

### 1. Why is this useful?

It helps organize APIs by resource or feature and keeps route definitions modular.

## 24. What is CORS?
CORS stands for Cross-Origin Resource Sharing. It's a browser security mechanism that controls whether a web application running on one origin can access resources from another origin. The server can specify which origins, methods, headers, and credentials are allowed through CORS repsonse headers.

```ts
app.use(
    cors({
        origin: "https://frontend.example.com"
    })
);
```
**Cross question**

### 1. Is CORD authentication?

No. CORS is a browser access-control mechanism. It doesn't authenticate users or authorize API operations.

### 2. Does CORD block Postman?

No. CORS is enforced by browsers. Tools such as Postman or server-to-server requests aren't subject to the browser's CORS enforcement.

## 25. What security measures would you add to an Express API ?
I would approach API security in multiple layers rather than relying on a single package. That incules input validation, authentication, authorization, secure headers, appropriate CORS configuration, rate limiting, HTTPS, secure cookies configuration where applicable, payload limits, safe error responses, secrets management, and proper logging and monioring.

**Cross question**

### 1. Is Helmet enough to secure Express?

No, Helmet mainly helps configure security-related HTTP headers, It doesn't handle authentication, authorization, validation, rate limiting, database security, or business-level vulnerabilities.

### 2. What's the first security mistake you would avoid?

I would avoid trusting client-controlled input. Every request should be trated as untrusted and validated according to the API contract and business rules.

## 26. What is rate limiting?
Rate limiting controls how frequently a client can access an API within a defined period. It's useful for protecting resources, reducing abuse, and limiting attacks such as brute-force attempts. In a distributed application, the rate-limit state usually needs to be shared rather than stored only in one Node.js process.

Example:
100 requests
per minute
per client

**Cross question**

### 1. Why isn't an in-memory rate limiter enough for multiple servers?

If we have multiple application instances, each instance would have its own memory. A client could therefore send requests across different instances and bypass the intended global limit. A shared store such as Redis can maintain the rate-limt state.

## 27. What is the difference between validation and sanitization?
validation determines whether input satisfies the expected rules, while sanitization transforms or cleans input into an appropriate form. Validation answers whether the data is acceptable; sanitization modifies the data where appropriate.

Example:

Validation: Is email valid?
sanitization: Trim whitespace from email.

**Cross question**

### 1. Is sanitization a replacement for validation?

No. Sanitization and validation solve different problems. Sanitizing input doesn't guarantee that the resulting data satisfies the application's requirements.

## 28. What happens if you trust req.body directly?
The request body is controlled by the client, so we should treat it as untrusted input. Directly passing it into database operations can allow unexpected fields or invalid values to reach the application. I would validate the payload and explicitly control which fields are accepted before passing data to the business or persistence layer.

Bad: 
```ts
User.create(req.body);
```

Better:
```ts
const { name, email } = req.body;

User.create({
    name,
    email
});
```

**Cross question**

### 1. Why not use TypeScript interfaces?

TypeScript types only provide compile-time checking. They don't validate data arriving from an HTTP request at runtime. External input requires runtime validation.

## 29. How would you desing a clean Express request flow?
I would separate the request pipeline into responsibilities. Common cross-cutting middleware can hanlde things such as security headers, request parsing, logging, and authentication. Routes map requests to controllers, controllers handle HTTP concerns, services or use cases handle application logic, repositories handle persistence, and centralized error handling converts failures into appropriate HTTP responses.

Request
   ↓
Security / CORS
   ↓
Body Parser
   ↓
Logger
   ↓
Authentication
   ↓
Router
   ↓
Validation
   ↓
Controller
   ↓
Service / Use Case
   ↓
Repository
   ↓
Database
   ↓
Response

**Cross question**

### 1. Does every Express project need all these layers?

No. The architecture should match the complexity of the application. For a small API, a controller and service may be enough. More layers become useful when the application has significant business logic, multiple data sources, or a larger team.

## 30. Practical: Create POST /users
For a user-creation enpoint, I would first validate the request body. The controller should handle the HTTP request and delegate the operation to a service. The service should contain the application logic, such as checking whether the user already exists, and the repository should handle the database operation. Errors should be passed to centralized error handling.

Flow: 

POST /users
    ↓
Validation
    ↓
Controller
    ↓
User Service
    ↓
User Repository
    ↓
MongoDB

Example: 
```ts
router.post(
    "/users",
    validationCreateUser,
    createUser
);
```

Controller:
```ts
const createUser = async (req, res, next) => {
    try {
        const user = await userService.createUser(req.body);

        res.status(201).json(user);
    } catch (error) {
        next(error);
    }
};
```

**Cross question**

### 1. Why return 201 instead of 200?

201 Created specifically indicates that the request successfully created a new resource. 200 is a general successful response, while 201 communicates the operation more precisely.

## 31. Where should duplicate-email checking happen?
I would perform an application-level check so that we can provide a meaningful error to the client, but I would not rely on that check alone. The database should also have a unique contraints or unique index because two requests can pass the application-level check concurrently.

Potential race:

Request A => email doesn't exist
Request B => email doesn't exist

Request A => insert
Request B => insert

The database constraint protects the final tntegrity.

**Cross question**

### 1. What if both requests pass the application check?

The unique database constraint should reject the conflicting write. The application should catch that database error and translate it into an appropriate conflict response.

## 32. Practical: Your API returns 500 for every error.
I would first distinguish between expected application errors and unexpected system errors. Knows errors should be mapped to appropriate HTTP status codes and safe messages, while unexpected errors should generally return a generic 500 response. Detailed error information should be logged internally but should not expose sensitive implementation details to the client.

Bad:
```json
{
    "error": "MongoError: connection string ... password ..."
}

Better:

```json
{
    "message": "Internal server error"
}
```

**Cross question**

### 1. Why shouldn't we send the actual error to the client?

Because internal error messages can expose implementation details, database information, stack traces, credentials, or other sensitive information that could help an attacker.

## 33. Common Express mistakes

1. Business logic inside controllers

Controller => everything

2. No centralized error handling 

Every controller has different error-response logic.

3. Trusting req.body

Client input is treated as trusted.

4. No runtime validation

TypeScript types are incorrectly assumed to validate HTTP input.

5. Wrong middleware order

Authentication/validation happens after the controller

6. Calling next() after sendong a response

Can result in duplicate response handling.

7. Exposing internal errors

Stack traces/database errors returned to clients.

8. In-memory state in horizontally scaled application

Each Node process has separate memory.

9. No payload limits

Clients can send unnecessarily large requests.

10. No database-level contraints

Application checks alone are used for data integrity.

## 34. How would you scale an Express application?
Express itself doesn't fundamentally change the scaling model of Node.js. I would typically keep the application stateless and run multiple Node.js instances behind a load balancer. Shared state such as sessions, caches, or rate-limit information should be stored in external system when necessary. Database performance, connection pooling, caching, background jobs, and observability also become important as traffic increase.

Architecture:

                 Load Balancer
                /      |      \
               ↓       ↓       ↓
           Express  Express  Express
               \       |       /
                \      |      /
                  MongoDB
                     +
                   Redis
                     +
                   Queue

**Cross question**

### 1. Why should the Express application be stateless?

Because any request can reach any application instance. If important state exists only in one process's memory, another instance won't have access to it. Externalizing shared state makes horizontal scaling much easier.

### 2. What if one server has a session stored in memory?

The next request may reach another server and that server won't have the session. We can use a shated session store such as Redis or use another stateless authentication approach such as appropriately desinged JWT-based authentication.

Final Exress mental model

                    CLIENT
                       ↓
                  HTTP Request
                       ↓
             ┌─────────────────┐
             │    Middleware   │
             │                 │
             │ CORS            │
             │ Security        │
             │ Logging         │
             │ Body parsing    │
             │ Authentication  │
             └────────┬────────┘
                      ↓
                   ROUTER
                      ↓
                VALIDATION
                      ↓
                 CONTROLLER
                      ↓
              SERVICE / USE CASE
                      ↓
                 REPOSITORY
                      ↓
                  DATABASE
                      ↓
                 RESPONSE
                      ↓
              ERROR HANDLER

| Layer              | Main responsibility                       |
| ------------------ | ----------------------------------------- |
| Middleware         | Request pipeline / cross-cutting concerns |
| Router             | Route mapping                             |
| Controller         | HTTP handling                             |
| Service / Use Case | Application/business logic                |
| Repository         | Data persistence                          |
| Database           | Data storage                              |
| Error Handler      | Centralized error response                |

Most important Express concepts to retain

Middleware → next() → request lifecycle → routing → params/query/body → validation → authentication → authorization → controller/service separation → async errors → centralized error handling → security → scaling.


# NestJS


## 1. What is NestJS?
NestJS is a framework for building scalable server-side applications with Node.js. It is built with TypeScript and provides a structured architecture around concepts such as modules, controllers, providers, and dependency injection. NestJS uses Express by default, although it can also work with Fastify. Its main purpose is to provide a consistent for building and maintaning larger backend applications.

Simple understanding

Express gives you building blocks:

Express 
|
|-- Router
|
|-- Middleware
|
|-- Request
|
|__ Response

NestJS adds a stronger application architecture:

NestJS
|-- Modules
|
|-- Controllers
|
|-- Providers
|
|-- Dependency Injection
|
|-- Guards
|
|-- Pipes
|
|-- Interceptors
|
|__ Exception Filters

Basic Nest controller:

```ts
import { Controller, Get } from "@nestjs/common"

@Controller('users')
export class UserController {
    @Get()
    getusers() {
        return [];
    }
}
```

**Cross question**

### 1. Is NestJS a replacement for Node.js?

No. Node.js is the runtime. NestJS is a framework that runs on Node.js.

### 2. Is NestJS a replacement for Express?

Not exactly. NestJS is a higher-level framework that can use Express as its underlying HTTP platform. NestJS provides additional architecture and abstractions on top of that platform.

## 2. Why use NestJS instead of Express?
Express is flexible and minumal, but it doesn't enforce a particular application architecture. As an application grows, teams need to establish their own conventions for dependency management, moduels, validation, authentication, error handling, and separation of responsibilities. NestJS provides these concepts as first class features, which makes large applications more structured and consistent. The tradeoff is that NestJS introduces more abstractions and conventions that a minimal Express.

Simple comparion

Express

Flexible 
Less opinionated
More manual architecture

NestJS

Structured
More opinionated
Built-in architectural patterns
Dependency Injection
Modules 
Guards
Pipes
Interceptors
Exception filters

**Cross question**

### 1. Is NestJS always better than Express?

It depends on the application. For a small API, Express may be simpler and have less overhead. For larger applications with multiple modules, developers, and business domains, NestJS's structure can make consistency and maintainability easier.

### 2. What problem is NestJS actually solving?

The main problem is application structure and maintainability rather than HTTP handling itself. Express already handles HTTP well. NestJS provides conventions and abstractions for organizing the application's business logic and cross-cutting concerns as complexity grows.

## 3. Explain the architecture of NestJS.
NestJS applications are organized primarily around moduels. Modules group related functionality. Controllers handle incoming requests, while providers contain reusable logic and are managed by Nest's dependency injection container. Additional components such as guards, pipes, interceptors, middleware, and exception filters handle cross-cutting concerns at different stages of the request lifecycle.

Basic architecture:

Module
|-- Controller 
|
|-- Providers
|
|__ Imports / Exports

Request:

Request => Middleware => Guards => Interceptors => Pipes => Controller => Service / Provider => Database

**Cross question**

### 1. What is the most important architectural concept in NestJS?

Modules and dependency injection are two of the core concepts. Modules organize the application into cohesive units, while dependency injection manages how those components depend on each other.

## 4. What is a Module in NestJS?
A module is a class decorated with @Module() that groups related controllers, providers, imports, and exports. modules help define the boundaries of different parts of the application and make dependencies explicit.

Example: 

```ts
@Module({
    controllers: [UserController],
    providers: [UserService],
})
export class UserModule {}
```

Simple understanding

Think:

UserModule
|
|-- UserController
|
|-- UserService
|
|__ UserRepository

Everything related to users can be organized together.

**Cross question**

### 1. Why do we need modules?

Modules provide a clear organizational boundary. They make it easier to understand which components belong together and which dependencies are available within a particular part of the application.

### 2. Can one module use another module?

Yes.
```ts
@Module({
    imports: [AuthModule],
})
export class UserModule {}
```

### 3. What s exports ?

The exports array specific which providers from a module are made available to modules that import it.

```ts
@Module({
    providers: [UserService],
    exports: [UserService],
})
export class UserModule {}
```

## 5. What is a Controller in NestJS?
A controller is responsible for handling incoming requests and returning reponses. It defines the HTTP routes for a particular resource and delegates application logic to providers or services instead of containing significant business logic itself.

Example:

```ts
@Controller('users')
export class UserController {

    constructor(
        private readonly userService: UserService,
    ) {}

    @Get()
    getUsers() {
        return this.userService.getUsers();
    }
}
```
**Cross question**

### 1. Should controllers contain business logic?

Generally no. Controllers should primarily handle HTTP concerns such as route parameters, request data, respinse status, and delegating work to services or use cases.

### 2. Why not put everything inside the controller?

Large controllers become difficult to test and maintain. Separating application logic into providers or use cases makes the logic reusable and keeps the HTTP layer thin.

## 6. What is a Provider?
A provider is a class or value that NestJS can manage through its dependency injection container. Services are the most common type of provider, but providers can also represent repositories, factores, configuration ojects, or other dependencies.

```ts
@Injectable()
export class UserService {
    getUser() {
        return [];
    }
}
```

Registered:

```ts
@Module({
    providers: [UserService],
})
export class UserModule {}
```

**Cross question**

### 1. Is every provider a service?

No. A service is a common type of provider, but providers can represent many kinds of dependencies, including repositories, factories, configuration values, and custom implemtations.

## 7. What is Dependency Injection in NestJS?
Dependency Injection is a desing pattern where a class receives the dependencies it needs from n external source instead of creating those dependencies itself. In NestJS, the dependency injection container manages these dependencies and injects them where they are required. This reduces coupling and makes components easier to test and replace.

Without DI:

```ts
class UserService {
    private repository = new UserRepositroy();
}
```
The service creates its own dependency.

With DI:
```ts
@Injectable()
class UserService {

    constructor(
        private readonly repository: UserRepository,
    ) {}
}
```
Nest creates and provides UserRepository

**Cross question**

### 1. Why is DI useful?

DI reduces tight coupling between classes, imporves testability, and makes implementations easier to replace. For exm, in tests I can provide a mock repository instead of using the real database repository.

### 2. Is DI specific to NestJS?

No. Dependency Injection is a general software desing patter. NestJS provides a built-in dependency injectioncontainer that makes impplementing it convenient.

## 8. What is @Injectable()?
@Injectable() marks a class as available to Nest's dependency injection system. It tells Nest that hte class an participate in dependency injection and can have depndencies injected into it.

```ts
@injectable()
export class UserService {}
```

**Cross question**

### 1. Does @Inectable() create an instance immediately?

No. It marks the class as injectable. Nest's depencency injection container manages
when and how the provider instance is created accoridng to is registration and scope.

## 9. What is a Service in NestJS?
A service is commonly used to contain application or business logic in a NestJS application. It is usually implemented as an injectable provider and is consumed by controller or other providers.

```ts
@Injectable()
export class UserService {

    async getUser(id: string) {

    }
}
```

Controller: 
```ts
@Controller('users')
export class UserController {

  constructor(
    private readonly userService: UserService,
  ) {}

  @Get(':id')
  getUser(@Param('id') id: string) {
    return this.userService.getUser(id);
  }
}
```

**Cross question**

### 1. Is "service" a NestJS requirement?

No. NestJS provides providers as the general dependency abstraction. Calling one provider a service is a common architectural convention for application logic.

### 2. Service vs Use Case?

A service is a broad term and can contain multiple related operations. A use case usually represents a specific application operation, such as CreateUser or PlaceOrder. Which approach to use depends on the application' complexity and architecture.

## 10. What is a DTO (Data Transfer Object)?
A DTO defines the structure of data that is transferred between the client and the application, usually for a specific operation such as creating or updating a resource. In NestJS, DTOs are commonly implemented as classes so that they can work with runtime validation and decorators.

```ts
export class CreateUserDto {
    name: string;
    email: string;
}
```

**Cross question**

### 1. Why use a class instead of an interface?

TypeScript interface are removed during compilation and don't exist at runtime. NestJS validation and transformation features often rely on runtime metadata and decorators, so DTOs are commonly represented as classes.

### 2. Does a DTO validate data automatically?

No. A DTO defines the expected structure, but runtime validation requires validation mechanisms such as Nest's validation pipe together with decorators or another validation solution.

## 11. What are Pipes in NestJS?
Pipes are components that operate an incoming data before it reaches the handler. They are commonly used for validation and transformation. For example, a pipe can validate a DTO or convert a route parameter from a string to a number.

```ts
@Get(':id')
getUser(
    @Param('id', ParseIntPipe) id: number,
) {
    return this.userService.getUser(id);
}
```

**Cross question**

### 1. What are the two major purposes of pipes?

Validation and transformation.

### 2. Give an example of transformation.

"123" => 123

Using: 
```ts
ParseIntPipe
```

### 3. Where can pipes be applied?

They can be applied globally, at the controller level, at the method level, or to individual parameters.

## 12. What is ValidationPipe?
ValidationPipe is NestJS's built-in pipe commonly used to validate incoming request data agains DTO validation rules. It can also tranform incoming values and remove or reject properties depending on its configuration.

```ts
app.useGlobalPipes(
    new ValidationPipe({
        whitelist: true,
        transform: true.
    }),
);
```

DTO:

```ts
export class CreateUserDto {

    @IsEmail()
    email: string;

    @IsString()
    name: string;
}
```
**Cross question**

### 1. What does whitelist: true do?

It removes properties that don't have corresponding validation decorators in the DTO.

### 2. What does transform: true do?

It enables transformation of incoming values into the expected types where Nest's transformation system can do so, and also allows DTO transformation behavior.

## 13. What are Guards?
Guards determine whether a request is allowed to continue to the route handler. They are commonly used for authentication and authorization. A guard returns a boolean or an appropriate asynchronous result, and Nest executes it before the controller handler.

```ts
@Injectable()
export class AuthGuard implements CanActive {

    canActive(contect: ExecutionContext): boolean {
        return true;
    }
}
```

```bash
Request
   ↓
Guard
   ↓
Allowed?
   ├── No → Reject
   └── Yes
        ↓
     Controller
```

**Cross question**

### 1. Guard vs Middleware?

Middleware operates earlier in the request pipeline and is genrally useful for generic request processing. Guards are specifically intergrated with Nest's execution context and are designed to determine whether a request can access a particular handler. This makes guards particularly suitable for authentication and authorization.

### 2. Guard vs Pipe?

Guards decide whether the request is allowed to continue, while pipes validate or transform incoming data.

## 14. What are Interceptors?
Interceptors wrap around the execution of a route handler and can execute logic before and after the handler. They are useful for cross-cutting concerns such as logging, response transformation, performache measurement, caching, and other behavior that needs access to the exectuion flow.

```bash
Request
   ↓
Interceptor BEFORE
   ↓
Controller
   ↓
Service
   ↓
Interceptor AFTER
   ↓
Response
```

**Cross question**

### 1. Can an interceptor transform the response?

Yes.
```ts
return next.handle().pipe(
    map(data => ({
        data,
    })),
);
```

## 15. What are Exception Filters?
Exception filters provide centralized control over how exceptions are handled and convertd into HTTP responses. They are useful when we need custom error-response behaviour, logging, or consistent error formatting across the application.

```ts
@Catch(HttpException)
export class HttpExceptionFilter
    implements ExceptionFilter {

        catch(exception: HttpException, host: ArgumentsHost) {

        }
    }
```

**Cross question**

### 1. Why use filters if Nest already handles exceptions?

Nest already provides default exception handling, so custom filters aren't always necessary. We use them when the application needs custom formatting, logging, mapping, or additional exception-handling behavior.

## 16. What are Decorators in NestJS?
Decorators are TypeScript language features used by NestJS to attach metadata or behavior to classes, methods, parameters, and properties. Nest uses decorators extensively to define controllers, routes, injectable providers, modules, and request parameters.

Exm.
```ts
@Controller()
@Injectable()
@Module()
@Get()
@Post()
@Body()
@Param()
```

**Cross question**

### 1. Is a decorator specific to NestJS?

No. Decorators are a language and metadata mechanism used by TypeScript and various frameworks. NestJS uses them heavily as part of its programming model.

### 2. What does @Controller('users') do?

It makes the class as NestJS controller and defines the base route prefix for the controller.

## 17. Explain the NestJS request lifecycle.

A NestJS request passes throught several stages before the controller executes. Middlewares can process the request first, guards determine whether it can continue, interceptors can wrap the execution, pipes validate or transform incoming data, and then the controller handler executes. Exceptions can be handled by Nest's exception mechanism or custom filters. Interceptors can also process the response after the handler completes.

```bash
Request
   ↓
Middleware
   ↓
Guards
   ↓
Interceptors
   ↓
Pipes
   ↓
Controller
   ↓
Service
   ↓
Response
```
RMG IPC SR

**Cross question**

### 1. Why is understanding the lifecycle important?

Because it helps determine where a particular responsibility belongs. For example, authentication usually belongs in guards, validation in pipes, generic request logging in middleware or interceptors, and exception fornamtting in filters.

## 18. What are custom providers?
Custom providers allow NestJS to control how a dependency is created or what implementation should be injected. They are useful when we want to inject a value, factory-generated object, existing provider, or and implementation using a custom token.

```ts
{
    provide: "CONFIG",
    usevalue: {
        environment: "production",
    }
}
```

Then: 

```ts
constructor(
    @Inject('CONFIG')
    private readonly config: Config,
) {}
```

**Cross question**

### Why use custom tokens?

They allows us to decouple the consuming class from a concrete implementation and choose which implementation or value should be provided.

## 19. How does NestJS Dependency Injection help testing?
Because dependencies are injected rather than created directly inside the class, we can replace real dependencies with mocks or test implementations. For example, a service that depends on a repository can receive a mock repository during testing instead of connecting to real database.

```bash
Conceptually:

Production

UserService
    ↓
MongoUserRepository
```
```bash
Testing:

UserService
    ↓
MockUserRepository
```

**Cross question**

### 1. Why is this better than new Repository()?

If the service creates the repository itself, the dependency is tightly coupled to that implementation and becomes harder to replace. With dependency injection, the dependency can be substituted without changing the service.

## 20. What are dependency injection scopes?
Common scopes:

```bash
DEFAULT / Singleton
REQUEST
TRANSIENT
```

By default, Nest providers are singleton-scoped, meaning the same instance is reused within the application context. Request-scoped providers create and instance for each request, while transient providers create a new instance for each consumer that injects them.

**Cross question**

### 1. Why not make everything request-scoped?

Request-scoped providers have additional creation and lifecycle overhead and can affect performance and dependency behavior. Singleton scope is generally preferable unless the provider genuinely needs request-specific state.

## 21. What is the Repository Pattern?
The repository pattern abstracts data persistence operations from the application's business logic. The service or use case interacts with a repository rather than directly depending on database-specific operations. This reduces coupling and makes it easier to change persistence details or mock the data layer during testing.

Architecture:

Controller => Service / Use Case => Repository => MongoDB

**Cross question**

### 1. Does NestJS require the repository pattern?

Not necessarily. For a small application, introducing a repository layer may add unnecessary abstraction. The value depends on complexity, testing needs, persistence boundaries, and how likely the data-access logic is to grow or change.

## 22. How does validation work in NestJS?
A common NestJS validation approach is to define DTO classes with validation decorators and apply ValidationPipe. The pipe receives the incoming data, validates it against the DTO rules, and either passes valid data to the controller or throws a validation exception.

Flow:

```bash
Request
   ↓
DTO
   ↓
ValidationPipe
   ↓
Valid?
 ├── No → 400
 └── Yes
       ↓
   Controller
```

**Cross question**

### 1. Is TypeScript enough for validation?
No, TypeScript provies compile-time type checking, but HTTP input comes from outside the TypeScript type system. Runtime validation is required.

## 23. How would you implement authentication in NestJS?
I would separate authentication from authorization. Authentication would validate the user's credentials or token, commonly using a guard and an authentication service. After authentication, the user's identify and claims can be attached to the request or execution context. Authorization can then determine whether that user has permission to perform the requested operation.

Request
   ↓
Auth Guard
   ↓
Token validation
   ↓
User identity
   ↓
Authorization
   ↓
Controller

**Cross question**

### 1. Why use a Guard instead of Middleware?

Guards are better integrated with Nest's execution context and route metadata, which makes them more suitable for authentication and authorization decisions. Middleware is more generic and operated earlier in the request pipeline.

## 24. How would you connect NestJS to MongoDB?
NestJS doesn't provide its own database engine. We integrate MongoDB through a MongoDB library or adapter such as Mongoose or the native MongoDB driver. The database integration is normally encapsulated inside a module and exposted to the application through providers or repositories.

NestJS
   ↓
MongoDB module
   ↓
Mongoose / MongoDB Driver
   ↓
MongoDB

```ts
MongooseModule.forRoot(
    process.env.MONGO_URL
);
```

**Cross Question**

### 1. Should controllers directly query MongoDB?

Generally no. Controllers should delegate application logic to services or use cases, which can then use repositories or models for persistence.

## 25. How would you structure a NestJS project?

```bash
src/
├── modules/
│   ├── users/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── repositories/
│   │   ├── dto/
│   │   ├── schemas/
│   │   └── users.module.ts
│   │
│   ├── auth/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── guards/
│   │   └── auth.module.ts
│   │
│   └── orders/
│
├── common/
├── config/
├── database/
└── main.ts
```

For a larger NestJS application, I prefer organizing code around business features rather than putting all controllers, services, and repositories into global folders. Each feature owns its related components, while genuinely shared functionality can live in common or shared modules. This keeps module boundaries clearer as the application grows.

## 26. Feature-based vs layer-based architecture

Layer-based

```bash
controllers/
services/
repositories/
dto/
```

Feature-based

```bash
users/
    controller
    service
    repository
    dto

orders/
    controllers
    service
    repository
    dto
```

Layer-based organization groups files by technical responsibility, while feature-based organization groups them by business capability. Feature-based organization ofter scales better for larger applications because everything related to a feature is located toghether. However, the choice depends on team conventions and application complexity.

**Cross Question**

### 1. Is feature-based always better?

No. Architecture should fit the project. A small application may easier to understand with a simple layered structure, while a larger domain-drivers application can benifit from feature boundaries.

## 27. What is a NestJS Monorepo?
A NestJS monorepo allows multiple applications and reusable libraries to exist within one repository. This can be useful when an organization has multiple backend services or applications that share common libraries such as authentication, configuration, logging, database utilities, or shared contracts.

Conceptually:

```bash
apps/
|
|-- api/
|
|-- auth-service/
|
|__ notification-service/

libs/
|
|-- common/
|
|-- database/
|
|__ config/
```

**Cross Question**

### 1. Why use a monorepo?

It can make shared code management, dependency management, tooling, and coordinated changes easier across related applications. The tradeoff is that the repository and build system become more complex.

## 28. How would you handle errors in NestJS?
NestJS provides built-in exception handling, so application code can throw appropriate Nest HTTP exceptions and Nest can convert them  into HTTP responses. For application-wide custom behaviour, exception filters can be used to standardize error formatting, logging, or exception mapping.

Example:

```ts
throw new NotFoundException(
    'User not found'
);
```
**Cross Question**

### 1. Why not return error objects manually?

Using Nest exceptions keeps error handling consistent with the framework's request lifecycle and allows centralized handling through its exception mechanism.

## 29. How would you improve NestJS application performance?
I would first identify the actual bottlenect using metrics and profiling rather than optimizing blindly. Depending on the problem, I would look at database queries and indexes, unnecessary network calls, caching, event-loop blocking, searialization, request payload sizes, connection pools, and expensive synchronous operations. For CPU-heavy work, I would consider bachground jobs or worker threads.

**Cross Question**

### 1. Does NestJS make an application automatically scalable?

No. NestJS provides structure, but scalability still depends on application architecture, database desing, infrastructure, caching, queues, load balancing, and how the application handles state.

## 30. Practical scenario -- User Creation
I would define a DTO for the request, validate it using a validation pipe, then let the controller delegate the operation to a user service or use case. The service would apply business rules and use a repository for persistence. The database would enforce important data-integrity contraints such as unique email. Errors would be converted into appropriate HTTP exceptions.

Flow:

```bash
POST /users
     ↓
ValidationPipe
     ↓
UserController
     ↓
CreateUserUseCase
     ↓
UserRepository
     ↓
MongoDB
```

## 31. Practical scenario -- Authentication
I would use an authentication guard to protect the endpoint. The guard would extract and validate the credentials, establish the user's identify, and allow the request to continue if authentication succeeds. Authorization can then use roles or permissions to determine whether the authenticated user is allowed to perform the operation.

```bash
Request
   ↓
AuthGuard
   ↓
JWT validation
   ↓
Authenticated user
   ↓
Authorization
   ↓
Controller
```

## 32. Practical scenario -- External API is slow

Suppose:

```bash

Your API => Payment API => 10 seconds
```

I would first determine whether the external API call is actually required synchronously. If the operation doesn't need an immediate result, I would consider moving it to a background job or queue. If it mush be synchronous, I would use appropriate timenouts, controlled retries where safe, logging, monitoring, and potentially caching or circuit-breaking strategies depending on the dependency.

**Cross Question**

### 1. Why not just increase the timeout?

Increasing the timeout can make users wait longer and can cause resources to remain occupied. It may hide the underlying dependency problem rather than solving it.

## 33. Practical scenario -- Large Nest application

Suppose the application has: 

```bash
Users
Orders
Payments
Notifications
Reports
Authentication
```

A reasonable structure:

```bash
src/
├── modules/
│   ├── users/
│   ├── orders/
│   ├── payments/
│   ├── notifications/
│   ├── reports/
│   └── auth/
│
├── common/
├── config/
├── database/
└── main.ts
```

I would organize the application around business modules and keep each module responsible for its own controllers, application logic, persistence, and DTOs where appropriate. Shared functionality should only be extracted when it is genuinely shared. I would avoid creating a large global service or utility layer that every module depends on because that can create unnecessary coupling.

## 34. Most important NestJS comparison

Concept                         Main responsibility

Module                          Organizes dependencies/features
Controller                      Handles HTTP requests
Provider                        Injectable dependency
Service                         Common provider for            application/business login

DTO                             Defines transferred data
Pipe                            Validation/transformation
Guard                           Access decision
Interceptor                     Wraps execution
Middleware                      Request preprocessing
Exception Filter                Exception handling
Repository                      Persistence abstraction

The mental model:

                   REQUEST
                      ↓
                 Middleware
                      ↓
                    Guard
                      ↓
                 Interceptor
                      ↓
                    Pipe
                      ↓
                 Controller
                      ↓
              Service / Use Case
                      ↓
                  Repository
                      ↓
                   MongoDB
                      ↓
                 Interceptor
                      ↓
                  RESPONSE

          Exception → Exception Filter


# Next

## 1. What is Next.js and why would you use it instead of React?
React is mainly a UI library, whereas Next.js provides a complete framework around React.
With Next.js we get things like routing, server-side rendering, static generation, server components, API or route handlers, caching, image optimization, and SEO support out of the box.
So if I'm building a production application where things like SEO, performance, routing, server-side data fetching, and deployment architecture matter, I would generally prefer Next.js over using React alone.

**Cross Question**

### 1. What does Next.js actually add on top of React?

The biggest additions are the application architecture and server capabilities. React handles the UI layer, while Next.js handles things like routing, rendering strategies, server components, data fetching, caching, middleware, and production optimizations.

### 2. Can we build a complete application with only React?

Yes. React can be used to build the frontend completely, but we would need to choose and configure additional libraries or infrastructure for routing, SSR, SEO, API communication, and other requirements. Next.js provides many of these capabilities as part of the framework.

## 2. What is the difference between App Router and Pages Router?

Next.js has two routing architectures. The older one is Pages Router, which uses the pages directory, and the newer one is App Router, which uses the app directory.
App Router introduced React Server Components, layouts, nested routing, loading and error UI, route handlers, and more flexible server-side data handling.
For a new application, I would generally use App Router unless there is a specific reason to maintain the Pages Router.

**Cross Question**

### 1. Is Pages Router still supported ?

Yes. Existing applications can continue using it. But for new development, App router is the architecture Next.js is desinged around.

### 2. Can both routers exist in the same application?

Yes, Next.js supports having both during migration. But I would avoid unnecessarily maxing the two architectures because it increase complexity.

## 3. What are Server Components in Next.js
Server Components are components that execute on the server instead of being sent to the browser as JavaScript for execution.
The important benifit is that we can perform server-side operations, such as fetching data or accessing server-side resources, without sending that implementation to the client.
It can also reduce the amount of JavaScript that needs to be shipped to the broswer.

**Cross Question**

### 1. Are all App Router components Server Components

By default, yes. Components inside the App Router are Server Components unless we explicitly mark a component with 'use client'.

### 2. Why would you use a Client Component?

I use a Client Component when the components needs browser-side interactivity or client-only APIs. For example, useState, useEffect, event handlers, browser APIs, or client-side state management.

## 4. What is 'use client'?
'use client' tells Next.js that the component should be treated as a Client Component.
I use it when the component needs things that only work on the client, such as state, effects, event handlers, or browser APIs.
I try not to put 'use client' unnecessarily at the top level because it can move more of the component tree into the client side and increase the JavaScript send to the browser.

**Cross Question**

### 1. Can a Client Component import a Server Component?

Not in the normal direct-import pattern. The component boundaries have restrictions. A common approach is to keep server-side logic in Server Components and pass the resulting data or supported component composition into Client Components.

### 2. Can a Server Component import a Client Component?

Yes. That's a common pattern. For example, the page can fetch data on the server and then pass that data to an interactive Client Component.

## 5. Explain SSR, SSG, ISR and CSR.

Approach        Basic idea
SSR             Generate HTML on the server for a request
SSG             Generate content ahead of time
ISR             Reuse generated content and regenerate it
CSR             Render/fetch primarily in the broswer

SSR means the server generated the page when the request happens.
SSG means the content is generated ahead of time and can be served quickly.
ISR means the content is generated ahead of time and can be served quickly.
CSR means the browser does most of the rendering and data fetching after the initial page loads.
In Next.js, I don't choose one strategy globally. I choose the rendering and caching behaviour based on how frequently the data changes and whether the page needs SEO or fast initial rendering.

**Cross Question**

### 1. Give me an example of SSR.

A dashboard where the content depends heavily on the current request or authenticated user can be a candidate for server-side rendering.

### 2. Give me an example of SSG.

A documentation page or relatively stati marketing page is a good example because the content doesn't change frequently.

### 3. Give me an example of ISR.

A product or content page where the data changes periodically but doesn't need to be regenerated for every request is a good use case.

## 6. What is the difference between Server Component rendering and SSR?
They are related, but they're not the same thing
Server Components describe where the component code executes. SSR describes when and how HTML is generated for a request.
A Server Component can execute on the server, but that doesn't automatically mean I should think of the whole application as traditional SSR.
With the App Router, Next.js combines Server Components, streaming, caching, and different rendering strategies.

**Cross Question**

### 1. So does Server Component mean SSR?

No. Server component and SSR solve different problems. Server Components are primarily about component execution and reducing client-side JavaScript, while SSR is a rendering strategy.

## 7. How does data fething work in the App Router?
In the App Router, I can fetch data directly inside Server Components uing async functions.
This means I don't necessarily need to create a separate API endpoint just for a Server Component to call my own backend.
For example, a Server coponent can directly call a backend service or database through server-side code, depending on the architecture.

**Cross Question**

### 1. Why not fetch everything using useEffect?

If the data can be fetched on the server, doing it there can improve the intial page experience, SEO, and reduce client-side JavaScript and loading states. I use client-side fetching when the data genuinely needs to be managed in the browser.

## 8. How does caching work in Next.js
Caching in Next.js can happen at different levels, and this is an area where I need to be precise rather that assuming every fetch behaves the same way.
Depending on the Next.js version and configuration, data can be cached and revalidated, while rendered output can also be reused.
I decide the caching strategy based on how fresh the data needs to be. For example, stati content can be cached for longer, while user-specific or highly dynamic data should generally not be treated as shared static data.

**Cross Question**

### 1. What is revalidation?

Revalidation means allowing previously generated or cached data to be refreshed according to a defined strategy instead of rebuilding everything manually.

### 2. What is time-based revalidation?

It means we specify a period after which the cached data can be refreshed. This is useful when the data changes periodically rather than on every request.

## 9. What is revalidate?
revalidate defines how frequently cached data or generated content can be refreshed.
For example, if I have product information that doesn't need to be updated every second, I can use a revalidation period instead of fetching fresh data for every request.

```ts
fetch('https://api.example.com/products', {
    next: {
        revalidate: 60,
    },
});
```

The application can reuse the cached result and revalidate it according to the configured period.

**Cross Question**

### 1. What id I need fresh data on every request?

Then I would use a dynamic or uncached approach instead of using a long revalidation period.

## 10. What is the difference between revalidate and no-store?
revalidate allows caching with controlled freshness, while no-store tells Next.js not to cache that request's result.
So if my data can be slightly stale, revalidation is useful. If the data much always be fetched fresh, I would consider no-store or another dynamic strategy.

## 11. What are layouts in Next.js?
Layout allow us to define UI that is shared across multiple routes.
For example, if I have a dashboard with a sidebar, header, and navigation, I can put those shared elements in a layout instead of repeating them on every page.

**Cross Question**

### 1. Why are layouts useful?

They provide shared UI structure and avoid duplication. They also allow nested route sections to have their own layouts.

## 12. What is the difference between page.tsx and layout.tsx?
page.tsx represents the UI for a specific route, while layout.tsx represents shared UI around its child routes.
For example, /dashboard can have a dashboard page, while the dashboard layout can containe the sidebar and header shared by /dashboard, /dashboard/setting, and other child routes. 

## 13. Explain dynamic routes.
Dynamic routes allow the route segment to be treated as a parameter

For exm.
```bash
app/products/[id]/page.tsx
```

then /products/100 and /products/200 can use the same page component, with id representing the dynamic value.

**Cross Question**

### 1. What about multiple dynamic segments?

we have nested dynamic segments.

```bash
app/
└── users/
    └── [userId]/
        └── posts/
            └── [postId]/
                └── page.tsx
```

### 2. How does file-based routing work in Next.js?
Next.js uses the folder structure to define routes. A folder represents a route segment, and page.tsx inside that folder makes it accessible as a route.

Example:

```bash
app/
├── page.tsx
├── users/
│   └── page.tsx
└── users/
    └── profile/
        └── page.tsx
```

Routes: 
```bash
/
/users
/users/profile
```

### 3. What are route groups?

Route groups allow us to organize routes without adding that folder name to the URL.
We create them using parentheses.

```bash
app/
├── (auth)/
│   ├── login/
│   └── register/
└── dashboard/
```

The (auth) folder doesn't appear in the URL.

So: 

```bash
/auth/login
```

does not happen.

Instead:

```bash
/login
/register
```

### 4. What are parallel routes?

Parallel routes allow us to render multiple route segments or UI sections simultaneously within the same layout. They're useful for complex interfaces such as dashboards where different sections can have independent UI states.

### 5. What are intercepting routes?

Intercepting routes allow one route to be displayed inside the context of another route. A common example is opening a product or imagein a modal while still keeping the underlying page visible.
It allows us to support both direct navigation to the page and modal-style navigation depending on how the user reaches the route.

## 14. What is a client component?
A Client Component is a component that needs to run in the browser. We use it when we need things such as state, effects, event handlers, or browser APIs.

```ts
'use client';

import { useState } from 'react';

export default function Counter() {
    const [count, setCount] = useState(0);

    return (
        <button onClick={() => setCount(count + 1)}>
        {count}
        </button>
    )
}
```

## 15. When should you use Server Component vs Client Component?
I start with a Server Component by default.

If the component needs browser-side state, effects, event handlers, or browser APIs, I make that specific component a Client Component.
I try to keep the Client Component boundary as small as practical.

**Cross Question**

### 1. Give me an example.

A product page can be a Server Component because it can fetch and display product information. But an Add to Cart button can be a Client Component because it needs user interaction and state.


## 16. What is hydration?
Hydration is when React takes the HTML that was already rendered and atteaches the necessary client-side behaviour to it.
It's what allows server-rendered UI to become interactive in the browser.

**Cross Question**

### 1. What causes hydration errors?

Usually there is a mismatch between what was rendered on the server and what React expects during the initial client render.
Common causes include browser-only APIs, random values, dates, inconsistent conditional rendering, or different data being used on the server and client.

## 17. Would you use React Query with Next.js?
Yes, when the application has substantial client-side server-state requirements. Reat Query is useful for things like caching, background refetching, mutations, loading states, and synchronization of server data on the client.
But I wouldn't automatically add it to every Next.js application.

## 18. Difference between <Link> and useRouter()?
I use Link for normal declarative navigation between pages.

I use useRouter when navigation needs to happen programmatically, usually after some user action.

```ts
<Link href="/dashboard">
    Dashboard
</Link>
```

Programmatic:

```ts
const router = useRouter();

router.push('/dashboard');
```

**Cross Question**

### 1. Which one would you prefer for a normal navigation link?

Link. It's designed specifically for navigation and provides Next.js routing optimizations.

## 19. What are usePathname() and useSearchParams()?
usePathname() gives me the current URL pathname, while useSearchParams() allows me to read query parameters from the URL.

Example:
```bash
/products?category=shoes
```

I can use useSearchParams() to read:

```bash
category = shoes
```

## 20. What is loading.tsx?
loading.tsx provides a loading UI for a route segment while its content is being prepared. It works well with the App Router's streaming and Suspense behavior.

## 21. What is error.tsx?
error.tsx provides an error boundary for a route segment. Instead of the entire application becoming unusable, we can show a controlled error UI for that section.

## 22. What is not-found.tsx?
not-foound.tsx provides the UI for cases where the requested resource doesn't exist.

## 23. How do you handle SEO in Next.js?
Next.js provides built-in support for metadata, server-side rendering, static generation, and other features that help search engines access page content.
I use the Metadata API for things like title, description, canonical information, and Open Graph metadata.

## 24. What is generateMetadata()?
generateMetadata allows metadata to be generated dynamically based on route parameters or fetched data.

```ts
export async function generateMetadata({
    params,
}: Props) {
    const { id } = await params;

    const product = await getProduct(id);

    return {
        title: product.name,
        description: product.description,
    };
}
```

**Cross Question**

### 1. Why not just put metadata directly in the page?

If the metadata is static, I can. But when the metadata depends on dynamic content, generateMetadata allows me to generate it based on the actua page data.

## 25. How do you optimize a Next.js application?
I first measure where the problem is. Then I look at things like unnecessary Client Components, JavaScript bundle size, images, fonts, data fetching, caching, rendering, third-party scripts, and unnecessary re-renders.
I don't blindly apply useMemo, useCallback, or lazy loading everywhere. I use them where profiling shows they provide value.

## 26. How does next/image improve performance?
The Next.js Image component provides optimizations such as appropriate image sizing, responsive behavior, lazy loading in  applicable cases, and image optimization.
It helps avid sending unnecessarily large images to the browser.

## 27. How would you debug a slow Next.js page?
I would first determine whether the problem is coming from the server, network, rendering, JavaScript excecution, or the backend API.
Then I would use browser performance tools, network analysis, bundle analysis, and application monitoring to identify the actual bottleneck.
I don't want to optimize based on assumptions.

## 28. What are server actions?
Server Actions allow client-side UI to trigger server-side functions directly through a defined server boundary.
They're useful for operations such as form submissions and mutations where I want to keep the server-side operation within the Next.js application architecture.

## 29. How would you use Server Actions with a form?
I can define a server action for the mutation and connect it to a form. The form can then trigger the server-side operation without me necessarily creating a separate API endpoint just for that form submission.

## 30. What is middleware used for in Next.js
From the frontend application perspective, middleware can intercept requests before they reach a route. Common uses include redirects, route protection flows, locale handling, rewrites, and request-based routing.

**Cross Question**

### 1. Should middleware contain all authentication logic?

No. Middleware can help with the routing flow, such as redirecting unauthenticated users, but sensitive authorization still needs to be enforced where the protected operation or resource is actually handled.

## 31. When would you use Context API?
I use Context when some state or configuration needs to be shared across a component tree and prop drilling becomes inconvenient.
Examples include theme, locale, or certain application-level UI state.

## 32. When would you use Redux or Zustand?
I would use a state management library when the application has complex shared client state that becomes difficult to manage with local state and Context.
I wouldn't introduce Redux or Zustand just because the application is large. The complexity of the state is what matters.

## 33. How do you type route parameters?
I explicitly type the params object so that the route parameters are known to TypeScript.

```ts
type Props = {
    params: Promise<{
        id: string;
    }>;
}

export default async function Page({ params }: Props) {
    const { id } = await params;

    return <div>{id}</div>
}
```

## 34. How do you type API response data?
I define a TypeScript type or interface for the expected response shape. For external data, I also prefer runtime validation when the data cannot be trusted purely based on TypeScript.

TypeScript disappears at runtime, so TypeScript types alone don't validate actual API responses.

## 35. Your entire Next.js application has "use client" in the root layout. What would you do?
I would investigate why the root needs to be a Client Component. If only a few parts need client-side functionality, I would move the client boundary down into those specific components.

## 36. A product page shows old product information after the backend data changes. What do you check?
First I would check the caching and revalidation behavior. I would identify whether the stale data is coming from Next.js caching, an API cache, CDM caching, or client-side state.
Then I would change the appropriate caching or revalidation strategy rather than simply forcing a browser refresh.

## 37. A page is slow even though the API response is fast. What do you investigate?
I would check the frontend side: JavaScript bundle size, hydration, unnecessary Client Components, expensive rendering, large images, third-party scripts, unnecessary state updates, and browser performance.
A fast API doesn't automatically mean a fast page.

## 38. A Server Component needs an interactive button. What would you do?
I would keep the main component as a Server Component and extract the button into a small Client Component.

## 39. You have 15 dashboard widgets and some are slow. How would you improve the UX?
I wouldn't make the user wait for every widget before showing the dashboard.
I would separate independent sections and use appropriate loading boundaries and streaming so that faster sections can render first while slower sections continue loading.

## 40. A hydration error appears only in production. How would you debug it?
I would compare the server output and inital client render and look for values that can differ between environments.
I would specifically investigate dates, random values, browser-only APIs, environment-dependent rendering, and conditional logic that produces different markup on the server and client.

# React Native

## 1. What is React Native?
React Native is a framework for building native mobile applications for Android and iOS using React and JavaScript or TypeScript. Instead of creating separate applications using Kotlin/Java for Android and Swift/Objective-C for iOS, we can share most of the application code between both platforms.

**Cross question**

### 1. When would we use React Native?

- We need both Android and iOS applications
- We want to share application logic and UI.
- The team already has React knowledge.
- We want faster development across both platforms.
- The application doesn't require everything to be written directly in native code.

## 2. Is React Native the same as React?
No. **React** is primarily a library for building user interfaces.
**React Native** uses React's programming model but provides native mobile components.

React                  React Native
Web                     Mobile
div                     view
span / p                Text
<img>                   Image
CSS                     StyleSheet /style objects
Browser DOM             Native UI
Browser APIs            Native/device APIs

## 3. Is React Native a WebView application?
No. React Native is different from a WebView-based application. A WebView essentially runs web content inside a mobile container, whereas React Native uses native UI components and communicates with the underlying mobile platform.

**Cross Question**

### 1. Why does this distination matter?

Because the rendering model, performancde characteristics, access to native APIs, and development approach are different. A WebView is essentially web content inside an application, while React Native is desinged to build the mobile UI using native platform capabilities.

## 4. What are the basic React Native components?
The most commonly used ones are:

```ts
View
Text
Image
TextInput
Pressable
ScrollView
Flatlist
SectionList
SafeAreaView
Modal
ActivityIndicator
KeyboardAvoidingView
```

## 5. Why can't we use normal HTML elements?
Because React Native dowesn't run inside the browser DOM.
React Native provides its own component system that maps to native platform UI.

## 6. How does React Native actually work?
At a high level:

```bash
Your TypeScript / JavaScript
            ↓
          React
            ↓
     React Native runtime
            ↓
      Native platform
        ↙          ↘
    Android         iOS
```

Our application logic is written using JavaScript/TypeScript and React.
React Native then coordinates rendering and communication with the native platform.
Modern React Native uses technologies such as JSI, Fabric, and TurboModules as part of its New Architecture.
We don't need to go deep into those yet. We'll cover them  later because they later because they become important when duscussing perfromance and native integration.

### 1. If React Native allows code sharing, does that mean we never write native Android/iOS code?

No. Most application code can be shared, but sometimes we need platform-specific code or native modules. For example, a device feature may require native Android or iOS APIs, or the platform behavior may be different. React Native allows us to isolate those differences instead of maintaining two completely separate applications.

### 2. why would you choose React Native instead of separate native Android and iOS applications?

The main advantage is code sharing. We can share a large portion of the UI, business logic, API integration, and state management between Android and iOS while still accessing native capabilities when required. This can reduce development and maintenance effort.

### 3. Does React Native provide native performance?

React Native can provide good native application performance, but performance depends on how the application is desinged. Expensive JavaScript operations, unnecessary re-renders, large lists, excessive bridge or native communication, and ineffcient animations can still create performance problems. For performance-sensitive areas, we need to understand the JavaScript and native sides separately.

### 4. What is the biggest difference between React and React Native?

The React programming model is similar, but the rendering environment is different React targets the browser DOM, while React Native targets native mobile components. That's why React concepts like components, props, state, and hooks are reusable, but elements such as View, Text, and Pressable are specific to React Native.

## 6. React Native vs Flutter?
Both React Native and Flutter are cross-platform tehnologies, but they use different approaches. React native uses React and JavaScript or TypeScript and integrates with native platform components, while Flutter uses Dart and its own rendering engine and widget system.


## 7. How does React Native work internally?
At a high level, we write our application using React and JavaScript or TypeScript. React manages the component tree, while React Native provides the runtime and native infrastructure required to render the UI and communicate with underlying Android or iOS platform. Modern React Native uses the New Architecture, including technologies such as JSI, Fabric, and TurboModules.

**Cross Question**

### 1. Is JavaScript directly drawing pixels on the screen?

Not in the same way a broswer renders HTML. React Native coordinates the React component tree with native platform rendering. The native side ultimately handles the actual platform UI rendering.

## 8. What does "native" mean in React Native?
Native means that the application can interact with the underlying Android or iOS platform and its native capabilities rather that being limited to browser APIs.
It means React Native can ultimately use native platform capabilities.

## 9. What happens when a React Native component renders?
When React renders a component, React creates and updates its component tree. React Native then coordinates those changes with its native rendering system, and the native platform renders the corresponding UI. The exact communication path depends on the React Native architecture and whether we're dealing with UI or native modules.

## 10. What are the JavaScript thread and UI thread?
React Native application involve JavaScript execution as well as native UI execution. JavaScript handles things such as application logic and React updates, while the natie side is responsible for rendering and platform-specific work. If we perform too much expensive work on the JavaScript side, it can affect responsiveness.

Simplified:

```bash
JavaScript side
----------------
React
State
Business logic
API processing
        |
        ↓
Native/UI side
----------------
Rendering
Gestures
Platform UI
```

Real-world example

```ts
const result = hugeArray.map(expensiveCalculation);
```

**Cross Question**

### 1. Does React Native automatically make every operation run on the UI thread?

No. We need to understand where the work is executed. Expensive JavaScript work can still block JavaScript execution, which can affect the user experience.

## 10. What was the React Native Bridge?
The Bridge was the traditional communication mechanism between the JavaScript side and the native side of React Native. JavaScript and native code communicated through serialized messages, which introduced overhead in certain scenarios.

**Cross Question**

### 1. Is the Bridge completely irrelevent today?

The old Bridge architecture is no longer the foundation of the New Architecture. When discussing modern React Native, I would focus on JSI, Fabric, and TurboModules rather than describing the bridge as the priamry architecture

## 11. What is JSI?
JSI stands for JavaScript Interface. It provides a lower-level interface that allows JavaScript to interact more directly with native C++ functionality without relying on the traditional serialized Bridge communication model.

```bash
Old architecture:

JavaScript
    ↓
 Bridge
    ↓
 Native


New Architecture:

JavaScript
    ↓
   JSI
    ↓
 C++ / Native
```

**Cross Question**

### 1. Why is it important?

It enables more efficient communication between JavaScript and native functionality.
This is particularly important for:
- performance-sensitive libraries
- animations
- native modules
- advanced native integrations

### 2. Does JSI mean JavaScript is no longer used?

No. JavaScript is still a major part of the application. JSI provides a more direct interface between JavaScript and native functionality.

## 12. What is Fabric?
Fabric is React Native's modern rendering system. It is part of the New architecture and improves how React's Component tree is translated into native UI, while also improving integration with modern React capabilities.

Think of it as the modern rendering infrastructure of React native.

```bash
React => Fabric => Native UI
```

**Cross Question**

### 1. Is Fabric the same thing as JSI?

No. JSI provides an interface between JavaScript and native or C++ functionality, while Fabric is the rendering system responsible for the modern React native UI architecture. They are related parts of the New Architecture but solve different problems.

## 13. What are TurboModules?
TurboModules are the modern native module system in React Native's New Architecture. They allow JavaScript to interact with native functionality more efficiently and support features such as lazy loading of native modules.

A native module could provide functionality such as:
- device information
- Bluetooth
- payments
- specialized hardware APIs

**Cross Question**

### 1. How are TurboModules different from Fabric?

TurboModules are primarily about native modules and accessing native functionality, while Fabric is focused on rendering the UI.

## 14. What is React Native's New Architecture?
The New Architecture is the modern React Natie architecture that includes technologies such as JSI, Fabric, TurboModules, and improved support for modern React capabilities. Its goal is to improve communication between JavaScript and native code, improve rendering, and provide a more flexible foundation for React Native.

At a high level:

```bash
              React Native
                   |
        -----------------------
        |          |          |
       JSI       Fabric   TurboModules
        |          |          |
     Native    Rendering    Native
```

**Cross Question**

### 1. Why should a React Native developer understand this?

Becasue native dependencies, performance issues, library compatibility, and upgrading React Native versions can depend on the underlying architecture. We don't need to implement these systems ourselves, but we sould understand what they are and how they affect application development.

## 15. When would you choose React Native?
I would consider React Native when the product needs Android and iOS applications and we want to share a significant amount of UI and business logic. It's especially useful when the team already has React and TypeScript knowlwdge and the application doesn't require everything to be implemented directly using platform-specific code.

## 16. When would you avoid React native?
I wouldn't choose React native blindly . If the application is heavily dependent on specialized native functionality, extremely platform-specific behaviour, or requirements that are difficult to satisfy reliable through React Native libraries or native modules, I would evaluate native development as well.

Examples might include application with:
- highly specialized hardware intergration
- platform-specific UI requirements
- extremely performance-sensitive workloads
-deep OS integration

**Cross Question**

### 1. Is performance alone a reason to reject React native?

Not necessarily. React Native can provide good performance when the application is desinged correctly. I would first identify the actual performance requirements and evaluate whether React native can satisfy them before deciding to use native development.

## 17. What are the advantages and disadvantages of React native?
The main advantage is that we can build Android and iOS applications using a largely shared codebase while still having access to native platform capabilities. It also allows React developers to use familiar concepts adn the TypeScript ecosystem. The trade-off is that we still have to deal with platform differences, antive dependencies, mobile-specific performance considerations, and sometimes native code.

**Advantages**
- Shared Android/iOS code
- React ecosystem
- TypeScript support
- Faster cross-platform development
- Large ecosystem
- Native API integration
- Shared business logic
- Expo ecosystem

**Challenges**
- Android/iOS differences
- native build configuration
- Native dependencies
- Performance optimization
- OS-specific behavior
- Dependency compatibility
- App-store release complexity

**Cross Question**

### 1. Explain React Native architecture in simple terms.

I would describe it as a React-based application layer that communicates with the native Android and iOS platforms. Modern React Native uses the New Architecture, which includes JSI for JavaScript-to-native interaction, Fabric for rendering, and TurboModules for native moduels. The goal is to make that interaction more efficient and better aligned with modern React.

### 2. If React Native is cross-platform, why do we still need Android and iOS knowledge?

Because cross-platform doesn't mean identical behavior across platforms. Permissions, lifecycle, navigation behavior, notifications, deep linking, storage, build systems, and OS restrictions can differ. A production React Native developer needs to understand those differences to troubleshoot and desing the application correctly.

### 3. What makes a React Native developer different from someone who only knows React?

React knowledge covers the components and state model, but React Native also requires understanding mobile UI, navigation, platform differences, permissions, native APIs, application lifecycle, performance constraints, build systems, and Android and iOS release processes.

### 4. Can we share 100% of React Native code between Android and iOS?

Usually no. We should aim to maximize shared code, but platform-specific behavior is sometimes necessary. We can isolate those differences using Platform APIs, platform-specific files, or native modules.

### 5. What happens if a third-party library only supports Android?

I would first check whether there is an equivalent cross-platform library or whether the library provides an iOS implementation. If the functionality is important, we can isoate the platform-specific implementation behind our own abstraction so the rest of the application doesn't depend directly on the platform-specific library.

### 6. What is the difference between a React Native library and a native module?

A React Native library can contain JavaScript or TypeScript code and may also contain native Android/iOS code. A native module specifically exposes platform functionality to the React Native application. Modern React Native uses TurboModules as the preferred native module architecture.

