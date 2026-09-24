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

No. Sanitization and validation solve different problems. Sanitizing input doesn't guarantee that the resulting data satisfies the applica