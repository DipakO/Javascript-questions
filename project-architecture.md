# Project Architectures

---

# 1. Monorepo Architecture

## What is Monorepo Architecture?

A **Monorepo** (Mono = Single, Repo = Repository) is a development setup where multiple applications and packages are stored and managed inside a **single Git repository**.

### Everything can live together:

1. Frontend applications
2. Backend services
3. Shared libraries
4. UI components
5. Authentication packages
6. Shared types
7. Configuration
8. Tooling

### Important:

> **Monorepo is a repository management strategy, not an application architecture.**

It mainly defines **how code is organized and managed**.

---

## Example Monorepo Structure

```text
apps/
 ├── web
 ├── admin
 ├── api
 └── mobile

packages/
 ├── ui
 ├── auth
 ├── config
 └── types
```

For example:

* `web` → Customer-facing application
* `admin` → Admin application
* `api` → Backend service
* `ui` → Shared UI components
* `auth` → Shared authentication logic
* `config` → Shared configuration
* `types` → Shared TypeScript types

---

## Why are Monorepos popular in large projects?

Monorepos help solve problems such as:

1. Duplicate code
2. Dependency mismatches
3. Difficult package publishing
4. Inconsistent tooling
5. Difficult cross-project refactoring
6. Duplicate configuration

For example, instead of having separate copies of a Button component in multiple repositories, we can keep one shared UI package:

```text
packages/
 └── ui/
      └── Button
```

Multiple applications can then use the same component.

---

## Advantages of Monorepo

1. Code sharing becomes easier.
2. Dependencies can be managed centrally.
3. Shared UI components can be reused.
4. Changes across multiple applications can be made in one repository.
5. Consistent linting, formatting, testing and build configuration.
6. Easier cross-project refactoring.
7. Easier collaboration between teams.

---

## Problems with Monorepos

1. Large repository size
2. Complex CI/CD
3. Team ownership issues
4. Dependency management can become complex
5. Requires good project structure and architecture
6. Poorly configured builds can become slow

---

## Popular Monorepo Tools

### 1. Nx

Enterprise-focused monorepo framework.

Provides:

* Dependency graph
* Build caching
* Task orchestration
* Code generation
* Affected project detection

### 2. Turborepo

Focused on fast builds and caching.

Commonly used with:

* React
* Next.js
* Node.js

### 3. pnpm Workspaces

Provides workspace and dependency management for multiple packages inside one repository.

### 4. Lerna

JavaScript/Node.js package management and monorepo tooling.

### 5. Bazel

Large-scale build and test system used for massive repositories and complex build pipelines.

---

## Interview Answer: What is a Monorepo?

> "A monorepo is a repository strategy where multiple applications and shared packages are maintained in a single Git repository. For example, we can have web and admin applications along with shared UI, authentication, configuration, and TypeScript packages. The main benefits are code sharing, consistent tooling, easier dependency management, and easier cross-project refactoring."

---

# 2. Microfrontend Architecture

## What is Microfrontend Architecture?

A **Microfrontend architecture** is a frontend architecture where a large frontend application is broken into multiple smaller, independently developed and potentially independently deployed frontend applications.

It is inspired by the **microservices architecture** approach.

Instead of having one giant frontend application, different business domains can be owned by different teams.

### Example: E-commerce Platform

```text
Main Shell
    |
    ├── Product Catalog
    ├── Recommendations
    ├── Cart
    ├── Payments
    └── Account
```

Different teams can own different domains.

For example:

* Product team → Product Catalog
* Recommendation team → Recommendations
* Cart team → Cart
* Payment team → Payments
* Account team → Account Management

---

## Why do Microfrontends exist?

As a frontend application becomes very large, problems can appear:

1. Deployment becomes risky.
2. Teams block each other.
3. Codebase becomes huge.
4. Development becomes slower.
5. Different teams may have different release cycles.

Microfrontends attempt to solve these problems by dividing the application according to business domains.

---

## Core Characteristics of Microfrontends

### 1. Independent Teams

Different teams can own different frontend domains.

### 2. Independent Deployment

Individual frontend domains can potentially be deployed independently.

### 3. Runtime Composition

A main shell/container application can load different microfrontends at runtime.

### 4. Technology Independence

Different microfrontends can potentially use different technologies.

For example:

```text
Product → React
Checkout → Angular
Account → Vue
```

However, using different technologies should be considered carefully because it can increase complexity.

---

# 3. Microfrontend Architecture Styles

Common approaches include:

### 1. Build-Time Integration

Microfrontends are combined during the build process.

### 2. Runtime Integration

Microfrontends are loaded dynamically at runtime.

### 3. iframe-Based Integration

Individual applications are loaded inside iframes.

### 4. Web Components

Microfrontends expose functionality through Web Components.

### 5. Module Federation

Module Federation allows applications to share and load modules at runtime.

It is one of the commonly used approaches for implementing runtime microfrontends.

---

# 4. Communication Between Microfrontends

Communication between microfrontends can become challenging because each microfrontend may be independently developed.

Common approaches:

1. Shared state
2. Event bus
3. URL-based communication
4. Custom browser events
5. Shared Redux store
6. Shared libraries/utilities

### Important consideration

We should avoid tightly coupling microfrontends because the main benefit is their independence.

---

# 5. Problems with Microfrontends

1. Increased architectural complexity
2. Harder debugging
3. Performance overhead
4. Developer experience can become more complex
5. UI consistency can be difficult
6. Dependency/version management
7. Communication between microfrontends
8. More complicated CI/CD and deployment
9. Duplicate dependencies can increase bundle size

---

# 6. Microservices Architecture

Microservices is a **backend architecture approach** where an application is divided into multiple smaller services.

Each service generally represents a specific business capability and can be developed, deployed, and scaled independently.

### Example

```text
E-commerce Backend

User Service
     |
Product Service
     |
Order Service
     |
Payment Service
     |
Notification Service
```

Each service can have its own:

* Business logic
* API
* Deployment
* Database or data ownership
* Scaling strategy

---

# 7. Microfrontend vs Microservices vs Monorepo

These three concepts solve different problems.

### Microfrontend

Used for **frontend architecture**.

```text
Frontend
 ├── Product
 ├── Cart
 ├── Checkout
 └── Account
```

### Microservices

Used for **backend architecture**.

```text
Backend
 ├── User Service
 ├── Product Service
 ├── Order Service
 └── Payment Service
```

### Monorepo

Used for **repository/code organization**.

```text
Single Git Repository

apps/
 ├── web
 ├── admin
 ├── api
 └── checkout

packages/
 ├── ui
 ├── auth
 └── types
```

### Important Interview Point

> "Microfrontend and microservices describe how an application can be divided into independently owned domains, while monorepo describes how the code is organized and managed in repositories."

---

# 8. Can We Use Monorepo + Microfrontend + Microservices Together?

Yes.

A large application can use all three approaches.

For example:

```text
                    Monorepo
                       |
        ┌──────────────┴──────────────┐
        |                             |
   Frontend                        Backend
        |                             |
 Microfrontends                  Microservices
        |                             |
 Product                         Product Service
 Cart                            Order Service
 Checkout                        Payment Service
 Account                         User Service
```

### Example

```text
apps/
 ├── shell
 ├── product
 ├── cart
 ├── checkout
 ├── admin
 ├── user-service
 ├── order-service
 └── payment-service

packages/
 ├── ui
 ├── auth
 ├── types
 └── config
```

The repository structure and runtime architecture are separate concerns.

---

# Module Federation

## 9. What is Module Federation?

**Module Federation** is a runtime code-sharing mechanism introduced with **Webpack 5**.

It allows one application to load modules or code from another application at runtime.

This is commonly used to implement **Microfrontend architectures**.

### Simple Definition

> "Module Federation allows multiple independently built applications to share and consume modules at runtime."

---

# 10. Core Concepts of Module Federation

## 1. Host

The **Host** is the main application that consumes modules from other applications.

Example:

```text
Host / Shell Application
        |
        ├── Product Remote
        ├── Cart Remote
        └── Checkout Remote
```

---

## 2. Remote

A **Remote** is an application that exposes modules that can be consumed by another application.

Example:

```text
Product Application
        |
        └── Exposes ProductPage
```

The Host can then consume the exposed module.

---

## 3. Exposed Modules

A remote application decides which modules/components should be available to other applications.

For example:

```text
Remote App
   |
   ├── ProductPage
   ├── ProductCard
   └── ProductDetails
```

Only selected modules need to be exposed.

---

## 4. Shared Dependencies

Common dependencies can be shared between applications.

For example:

```text
React
React DOM
React Router
```

Instead of loading multiple copies unnecessarily, applications can share dependencies when configured appropriately.

---

# 11. How Module Federation Works

Simple flow:

```text
Host Application
       |
       | Load remote module
       ↓
Remote Application
       |
       | Exposes module
       ↓
ProductPage / Component
```

### Step-by-step:

1. The Host application starts.
2. Host knows where the Remote application is available.
3. Host requests the remote module.
4. Remote exposes the requested module.
5. Host loads the module at runtime.
6. The module becomes part of the Host application UI.

---

# 12. Why use Module Federation?

Module Federation can provide:

1. Runtime code sharing
2. Independent deployment
3. Independent development
4. Microfrontend implementation
5. Shared dependencies
6. Ability to load remote modules dynamically

---

# 13. Module Federation Interview Answer

> "Module Federation is a runtime code-sharing mechanism introduced in Webpack 5. It allows independently built applications to expose and consume modules at runtime. In a microfrontend architecture, we can have a Host or Shell application that loads Remote applications such as Product, Cart, or Checkout. The Remote exposes specific modules, and the Host consumes them at runtime. Shared dependencies such as React can also be configured to avoid unnecessary duplication."

---

# 14. Monorepo vs Microfrontend

This is an important interview question.

| Monorepo                                    | Microfrontend                                                |
| ------------------------------------------- | ------------------------------------------------------------ |
| Repository strategy                         | Frontend architecture strategy                               |
| Defines how code is organized               | Defines how frontend is divided                              |
| Multiple apps/packages can live in one repo | Multiple frontend domains/apps                               |
| Does not require independent deployment     | Often designed for independent deployment                    |
| Can share code easily                       | Focuses on team/domain independence                          |
| Can be used without microfrontends          | Can be implemented with separate repositories                |
| Tools: Nx, Turborepo, pnpm                  | Tools/approaches: Module Federation, Web Components, iframes |

### Important Point

> "Monorepo and Microfrontend are not alternatives. A company can use a monorepo to manage multiple microfrontends."

---

# 15. Microfrontend vs Traditional Frontend

### Traditional Frontend

```text
One Large Application
        |
 ┌──────┼──────┐
Product Cart Checkout
```

Usually:

* One codebase
* One deployment pipeline
* Strong coupling between teams

### Microfrontend

```text
Main Shell
    |
 ┌──┼───────────┐
Product   Cart   Checkout
   |        |        |
Team A    Team B   Team C
```

Each domain can have more independent ownership and release cycles.

---

# 16. When should we use Microfrontends?

Microfrontends can be considered when:

1. The frontend is very large.
2. Multiple teams work on different business domains.
3. Teams need more independent release cycles.
4. Different domains have different ownership.
5. Independent deployment is an important requirement.

For a small or medium application, microfrontends may introduce unnecessary complexity.

---

# 17. When should we use a Monorepo?

A monorepo can be useful when:

1. Multiple applications share code.
2. Teams need shared UI components.
3. Applications share TypeScript types.
4. Consistent tooling is required.
5. Cross-project changes are common.
6. Multiple packages need to be developed together.

---

# 18. Quick Interview Revision

### Monorepo

> **"Multiple applications and packages in one repository."**

### Microfrontend

> **"Large frontend divided into independently owned frontend domains."**

### Microservices

> **"Backend divided into independently developed services."**

### Module Federation

> **"Runtime mechanism for sharing and consuming modules between applications."**

### Host

> **"Application that consumes remote modules."**

### Remote

> **"Application that exposes modules."**

### Exposed Module

> **"A module made available by a Remote application."**

### Shared Dependency

> **"Common dependency configured to be shared between applications."**

### Easy Architecture Example

```text
                 MONOREPO
                    |
        ┌───────────┴───────────┐
        |                       |
     FRONTEND                BACKEND
        |                       |
 MICROFRONTENDS             MICROSERVICES
        |                       |
  ┌─────┼─────┐          ┌──────┼──────┐
Product Cart Checkout   User  Order  Payment
        |
   Module Federation
        |
   Host + Remotes
```
