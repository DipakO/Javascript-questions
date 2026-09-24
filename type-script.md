# TypeScript

### 1. What is TypeScript ?

**Answer:** TypeScript is a statically types superset of JavaScript developed by Microsoft. If adds features such as static typing, interfaces, generics, enums, and advanced type-system capabilities on top of JavaScript runs. The main benefit is that it can catch many type-related errors during development and makes large codebases easier to maintain.

**Cross-question**

#### i ). Is TypeScript a programming language?

**Answer:** Yes. TypeScript is a programming language built as a superset of JavaScript. it extends JavaScript with a static type system and additional language features, and ultimately gets transformed into JavaScript.

#### ii ). Does TypeScript provide runtime type safety?

**Answer:** No, not by itself. TypeScript's type checking happens at compile time and the types are generally erased from the negated JavaScript. If I receive untrusted runtime data, such as an API response, I still need runtime validation if I want to verify it's actual shape.

### 2. Why use TypeScript instead of JavaScript?

**Answer:** The main reason is maintainability and developer safety, especially in larger application. Static typing helps catch incorrect assumptions during development, improves IDE support and refactoring, and makes APIs and component contracts clearer. it doesn't eliminate runtime errors, but it reduces an important category of errors before the code reaches production.

**Cross-question**

#### i ) Does TypeScript make code completely bug-free ?

**Answer:** No, TypeScript mainly catches type-related problems at compile time. it doesn't automatically catch business-logic bugs, incorrect runtime data, network failures, or every possible runtime issue.

#### ii ) What are the disadvantages ?

**Answer:** The main disadvantages are the additional learning curve, compilation and configuration overhead, and the possibility of writing overly complex types. If TypeScript is used excessively or poorly, the type system itself can become difficult to maintain.

### 3. What is static typing ?

**Answer:** Static typing means types are checked during development or compilation rather than only when the program is running. In TypeScript, the compiler can determine that a variable, parameter or return value is expected to have a particular type and report incompatible usage before execution.

**Cross-question**

#### i ) Is JavaScript dynamically typed ?

**Answer:** Yes. JavaScript is dynamically typed, meaning values have types at runtime and a variable can hold values of different types during execution.

### 4. What is type interface ?

**Answer:** Type interface is TypeScript's ability to determine a value's type without requiring an explicit type annotation. TypeScript analyzes the value surrounding context and infers the most appropriate type.

**Cross-question**

#### i ) Should we explicitly type everything?

**Answer:** No, Explicit annotations are useful when they communicate intent or define an important contract, but unnecessary annotations can add noise. I generally rely on interface when TypeScript can determine the type clearly and use explicit types at boundaries such as function parameters, public APIs and complex data structures.

### 5. What is type annotation?

**Answer:** A type annotation explicitly tells TypeScript what type a variable, parameter, property or return value is expected to have.

**Cross-question**

#### i ) Annotation vs interface ?

**Answer:** Interface means TypeScript determines the type automatically, while annotation means I explicitly specify the expected type.

### 6. What is structural typing?

**Answer:** TypeScript primarily uses structural typing, which means type compatibility is based on the structure or shape of the types rather than their explicit names or declarations. If and object has reuired properties with compatible types, it can generally be assigned to another compatible object type.

**Cross-question**

#### i ) Why is this called structural typing?

**Answer:** Because TypeScript checks the structure of the value rather than requiring the value to explicitly declare that it implements a particular interface.

#### ii ) Is TypeScript nominally typed?

**Answer:** No, TypeScript is primarily structurally types, although there are techniques such as branding or unique symbols that can be used to create nominal-like behaviour.

## PART 2 — any, unknown, never, void

### 7. What is any?

**Answer:** any effectively tells TypeScript to stop performing meaningful type checking for that value. It provides maximum flexibility but removes much of the safety that TypeScript provides, so I avoid it unless there's a specific reason to use it.

**Cross-question**

#### i ) Why is any dangerous ?

Because it allows incompatible operations without compiler errors and can allow type errors to propagate through the application. Excessive use of any essentially turns parts of a TypeScript codebase back into dynamically types JavaScript.

### 8. What is unknown?

**Answer:** unknown represents a value whose type we don't know yet. Unlike any, TypeScript doesn't allow arbitrary operations on an unknown value until we narrow or validate its type. That's why unknown is generally safer when dealing with data whose type isn't known.

**Cross-question**

#### i ) any vs unknown?

any disables type checking for the value, whereas unknowns forces me to establish the value's type before performing type-specific operations. So for untrusted or unknown data, i prefer unknown.

### 9. What is never?

**Answer:** never represents a value that can never occur. It's commonly used for functions that never successfully return, such as functions that always throw an error or run indefinitely. It's also useful for exhaustive checking of discriminated unions.

**Cross-question**

#### i ) never vs void

**Answer:** void means a function completes but doesn't return a meaningful value. never means the function doesn't complete normally at all.

### 10. What is void?

**Answer:** void is commonly used as the return type of a function that doesn't return a meaningful value.

**Cross-question**

#### i ) Is void the same as undefined?

**Answer:** They're related but not identical. undefined is an actual JavaScript value, while void is primarily a TypeScript type used to describe functions whose return value isn't intended to be used.

## PART 3 — type vs interface

1. Type vs Interface:

Both type and interface can define object shapes. Interfaces are primarily useful for object contracts and support for object contracts and support features such as extension and declaration merging. Type aliases are more flexible because type can represent unions, intersections, tuples, primitives and other type expressions. In practice, i use interfaces when I'm defining an extensible object contract, and types when I need more complex type composition, while also following the conventions of the existing codebase.

**Cross-question**

#### i) So if both can define objects, which one do you prefer ?

**Answer:** For object-shaped contracts, I generally prefer interface, especially when I expect the contract to be extended or implemented by classes. For unions, intersections, tuples or more complex type

compositions, i use type. But I don't consider the choice to be an absolute rule; consistency within the project is also important.

#### ii) Can an Interface extend another interface ?

Yes:

```ts

interface User {

```

id: string;

```ts

}

interface Admin extends User {

permissions: string[];

}

```

Yes, Interfaces support extension using extends, which is useful when building hierarchical object contracts.

#### iii) Can a type extend another type ?

**Answer:**

```ts

type User = {

```

id: string;

```ts

}

type Admin = User & {

permissions: string[];

}

```

A type alias doesn't use extends in the same way an interface does, but object types can be composed using intersection types with &.

#### iv) Can an interface represent a union ?

**Answer:** Type aliases are better suited for union and intersection compositions. For example, a type alias can represent a union of literal values, which an interface cannot directly express.

**This Works:**

```ts

type Status = "loading" | "success" | "error";

```

You can't replace that directly with

```ts

interface Status {

}

```

#### v) Declaration merging.

**Answer:** One important difference is that interfaces support declaration merging. If the same interface is declared multiple times in the same scope, TypeScript merges the declarations. Type aliases don't support declaration merging.

```ts

interface user {

```

name: string;

```ts

}

interface user {

```

age: string;

```ts

}

```

TypeScript effectively combines them.

**So:**

```ts

const user: User = {

```

name: "XYZ",

age: 30

```ts

};

```

works.

This is called declaration merging.

#### vi) Where is declaration merging actually useful ?

**Answer:** A practical use case is type augmentation. For example, when a third-party library exposes an interface and I need to add application-specific properties, declaration merging can allow me to extend that existing type safely.

#### vii) can a interface extend a type ?

**Answer:** Yes, with restrictions.

```ts

type user {

```

name: string;

```ts

}

interface Admin extends User {

permissions: string[];

}

```

This works when the type being extended has a statically known object-like structure.

But you can't do something like:

```ts

type Status = "active" | "inactive";

// interface Admin extends Status {}

```

Because a union isn;t an object contract that an interface can extend.

An interface can extend an object-like type alias, but it cannot extend arbitrary type expressions such as unions or primitive types.

#### viii) Which one is better for React props ?

**Answer:** For React props, both are valid. I usually use whichever convention the codebase follows. if the props are a straightforward object contract, an interface is a reasonable choice; if I'm composing props with unions or intersections, a type alias can be more convenient.

#### ix) Real- word

Suppose you have different API responses based on status. Would you use interface or type?

**Answer:** This is where type becomes very useful.

```ts

type ApiResponse =

| {

```

status: "success";

```ts

data: User[];

}

| {

```

status: "error";

message: string;

```ts

};

```

Now Typescript can understand the relationship between status and the available properties.

For a response that can have multiple distinct shapes, I'd use a discriminated union with a type alias. That allows TypeScript to narrow the response based on a common discriminator such as status.

#### x) So should I always use interface for objects and type for everything else ?

**Answer:** No That's a useful rule of thumb, but not a hard rule. Both can describe object shapes. I would consider the requirements, whether declaration merging or interface extension is useful, whether I'm composing unions or intersections, and the conventions already established in the codebase.

## PART 4 — Union & Intersection

### 14. What is a union type?

**Answer:** A union type allows a value to be one of several possible types. We use the pipe operator to define it.

**Cross-question**

#### i ) How do you safely use a union?

**Answer:** A narrow type type before performing operations that are specific to one member of the union.

### 15. What is an intersection type?

**Answer:** An intersection combines multiple types into a single type that must satisfy all of them.

**Cross-question**

#### i ) Union vs intersection?

**Answer:** A union means the value can satisfy one of several possible types, while an intersection means the value must satisfy all the combined types.

### 16. What happens when you intersect incompatible types?

**Answer:**

```ts

type A = {

```

id: string;

```ts

}

type B = {

```

id: number;

```ts

};

type C = A & B;

```

C effectively requires:

id: string & number

which can't be satisfied normally.

When incompatible property types are intersected, the resulting type can becomes impossible to contruct because the property mush satisfy both constraints simultaneously.

## PART 5 — Generics

### 17. What are generics?

**Answer:** Generics allow us to write reusable code while preserving type information. Instead of fixing a function or component to one specific type, we define a type parameter and allow TypeScript to determine or receive the actual type when the code is used.

```ts

function identity<T>(value: T): T {

return value;

}

```

**Cross-question**

#### i ) Why not use any ?

**Answer:** any would allow different types but would lose the relationship between the input and output. With a generic, if I pass a string, TypeScript knows the result is a string; If I pass a number, the result is a number.

### 18. What is generic inference?

**Answer:**

```ts

function identify<T>(value: T): T {

return value;

}

const result = identity("hello");

```

TypeScript infers:

```ts

T = string.

```

Generic inference allows TypeScript to determine the generic type parameter from the arguments or context, so I don't always need to explicitly provide the type.

### 19. What are generic constraints?

**Answer:** A generic constraint limits what types can be used for a generic parameter. here, I extends { id: string } means that whatever type is passed must contain an id property of type string.

**Cross-question**

#### i ) Does extends here mean inheritance ?

**Answer:** Not exactly. In a generic constraint, extends means the type must satisfy or be assignable to the specified constraint. It's different from class inheritance.

### 20. Can generics have multiple parameters?

**Answer:** Yes,

```ts

function pair<T, U>(first: T, second: U) {

return {

```

first,

second,

```ts

};

}

```

Yes, A generic function can have multiple type parameters when the relationship between multiple values needs to be preserved.

### 21. What is a generic interface?

**Answer:**

```ts

interface ApiResponse<T> {

```

data: T;

success: Boolean;

```ts

}

```

**Then:**

```ts

type UserResponse = ApiResponse<User>;

```

A generic interface allows the same structural contract to be reused with different data types while preserving type safety.

### 22. How would you type an API response?

**Answer:**

I'd use a generic response type when the response envelope is consistent but the actual data changes between endpoints. This avoids duplicating the response structure while keeping the specific data strongly typed.

**Cross-question**

#### i ) Does this guarantee that the backend actually returned a valid User ?

**Answer:** No, This only tells TypeScript how we're treating the value at compile time. if the data comes from an external source, runtime validation is still needed if we need to guarantee its actual shape.

## PART 6 — Type Narrowing

### 23. What is type narrowing?

**Answer:** Type narrowing is the process by which TypeScript uses control-flow analysis and runtime checks to reduce a value from a broader type to a more specific type within a particular code path.

```ts

function print(value: string | number) {

```

if (typeof value === "string") {

value.toUpperCase();

```ts

}

}

```

inside the if, TypeScript knows value is a string.

### 24. What are type guards?

**Answer:** A type guard is a condition or function that provides TypeScript with information that allows it to narrow a value to a more specific type.

**Examples include:**

typeof

instanceof

in

and custom type guards.

### 25. What is a custom type guard?

**Answer:**

**Exm:**

```ts

function isUser(value: unknown): value is User {

return (

```

typeof value === "object" &&

value !== null &&

"id" in value

);

```ts

}

```

A custom type guard is a function whose return type uses the value is Type syntax. it tells TypeScript that when the function returns true, the value can be treated as that specific type.

**Cross-question**

#### i ) Does this function actually validate every property of user?

**Answer:** Not necessarily. The implementation determines how much validation is performed. The type predicate tells TypeScript what the function claims, so the runtime check should accurately enforce that claim.

## PART 7 — Utility Types

### 26. What are utility types?

**Answer:** Utility types are built-in generic types provided by TypeScript that allow us to transform or construct new types existing types. They reduce duplication and are especially useful when defining variations of existing models.

Common ones: partial, Required, Readonly, Pick, Omit, Record, Exclude, Extract, NonMullable, ReturnType, Parameters, Awaited.

### 27. What is Partial<T>?

**Answer:**

```ts

interface User {

```

name: string;

email: string;

```ts

}

type UpdateUser = Partial<User>;

```

Now both are optional.

Partial<T> creates a type where all properties of T become optional. It's commonly useful for update or patch operations.

### 28. Pick vs Omit?

**Answer:**

```ts

type UserPreviee = Pick<User, *"name"* | *"email"*>;

```

Pick selects.

```ts

type PublicUser = Omit<User, *"password"*>;

```

Omit removes.

Pick creates a type containing only the specified properties, while Omit creates a type containing everything exce[t the specified properties.

### 29. What is Record?

**Answer:**

```ts

type UserRoles = Record<string, string[]>;

```

Record<k, T> creates an object type whose keys are of type K and whose values are of type T. It's useful when I want to model dictionaries or maps with known key and value types.

### 30. What is ReturnType?

**Answer:**

```ts

function getUser() {

return {

```

id: "1",

name: "John",

```ts

};

}

type User = ReturnType<typeof getUser>;

```

ReturnType extracts the return type of a function type. It's useful when I want to derive a type from an existing implementation rather then duplicating the return structure.

## PART 8 — keyof, typeof

### 31. What does keyof do?

**Answer:**

```ts

interface User {

```

id: string;

name: string;

```ts

}

type UserKeys = keyof User;

```

**Result:**

```ts

"id" | "name"

```

keyof produces a union of the known property keys of a type.

**Cross-question**

```ts

type UserValue = User[keyof User];

```

This represents the union of the value types of all properties in User. In this example, it would be string, because both properties are strings.

### 32. What does typeof mean in TypeScript?
**Answer** : There are two contexts.

Runtime JavaScript:

```ts 
typeof value
```

TypeScript type context:

```ts

const user = {
    name: "John",
};

type User = typeof user;

```

In a type context, TypeScript's typeof can derive a type from an existing value. This is different from JavaScript's runtime typeof operator, which returns a string describing the runtime type.

## PART 9 -- Mapped Types.

### 33. What are mapped types?
**Answer**: Mapped types allow us to create a new type by iterating over the properties of an existing type and transforming those properties.

Example:

```ts
type Optional<> = {
    [k in keyof T]?: T[k];
};
```

This is conceptually similar to what Partial<T> does.

**Cross-question**

#### i) What does k in typeof T mean?
**Answer**: keyof T gives us keys of T, and k in keyof T iterates over those keys to construct the new type.

## PART 10 -- Conditional Types

### 34. What are conditional types?
**Answer**: Conditional types allow TypeScript to choose one type or another based on whether a type satisfies a condition. They use syntax similar to a type-level ternary operator.

```ts
type IsString<T> = T extends string ? true : false;
```

**Cross-question**

#### i) What does extends mean here?
**Answer**: Here, extends is checking whether T is assignable to string. It's a type-system condition, not class inheritance.

### 35. What are distributive conditional types?
**Answer**: 
```ts
type Toarray<T> = T extends unknown ? T[]: never;

type Result = ToArray<string | number>;
```
This distributes over the union.

A conditional type can distribute over a union when the checked type is a naked type parameter. That means the conditional is evealuated separately for each member of the union and the results are combined.

## PART 11 -- Discriminated Unions

### 36. What is a discriminated union?
**Answer**:
```ts
type Result = 
    | {
        status: "success";
        data: User;
    }
    | {
        status: "error";
        message: string;
    };
```
It's useful for modeling states such as API responses, asynchronous UI state, from states, reducer actions, or any domain where different states have different valid properties.

### 37. How do you achieve exhaustive checking?
**Answer**: 
```ts
function handle(result: Result) {
    switch (result.status) {
        case "success":
            return result.data;

        case "error":
            return result.message;
        
        default:
            return assertNever(result);
    }
}

function assertNever(value: never): never {
    throw new Error("Unexpected value");
}
```
I can use a never check in the default branch. If a new union member is added and isn't handled, TypeScript will report an error because the value is no longer never.

## PART 12 -- Function Types

### 38. How do you type a function?
**Answer**:
```ts
const add = (a: number, b: number): number => {
    return a + b;
};
```
I can explicitly type the parameters and return value. For reusable function contracts, I can also define a function type or interface.

```ts
type Calculator = (a: number, b: number) => number;
```

### 39. What are function overloads?
**Answer**: 
```ts
function format(value: string): string;
function format(value: number): string;

function format(value: string | number): string {
    return String(value);
}
```

Function overloads allow me to expose multilple valid call signatures for the same function while providing a single implementation. Type're useful when the realtionship between inut types and the rsulting API behaviour needs to be expressed clearly.

**Cross-question:**

#### i) Why not just use a union?
**Answer**: A union can work when the return type and behaviou are the same, but overloads are useful when different input types have different return types or when I want to provide more precise call-site type checking.

## PART 13 -- Type Assertions

### 40. What is a type assertion?
**Answer**: 
```ts
const value = input as string;
```

A type assertion tells TypeScript to trate a value as a specifc type. it doesn't perform runtime conversion or validation; it only changes how TypeScript analyzes that value.

**Corss-question**

#### i) Does as string convert the value to a string?
**Answer**: No, It doesn't convert anything at runtime. It's only a compile-time assertion.

### 41. as vs type conversion?
**Answer**:
```ts
const value = input as string;
```
doesn't convert.
Whereas: 
```ts
const value = String(input);
```
actually converts the value at runtime.

as affects TypeScript's type checking, while functions such as String() perform actual runtime conversion.

## PART 14 -- Optional / Readonly

### 42. What does ? mean in a property?
**Answer**:
```ts
interface User {
    name: string;
    age?: number;
}
```
It means the property is optional, so an object can omit it. When accessed, the property's type is generally treated as potentially undefined.

### 43. What does readonly do?
**Answer**: 
```ts
interface User {
    readonly id: string;
}
```
readonly prevents assignment to that property through TypeScript's type system after initialization. It's primarily a compile-time restriction; it doesn't automatically make the underlying JavaScript object deeply immutable at runtime.

**Cross-question**

#### i) Does readonly make nested objects immutable?
**Answer**: No, readonly is shallow unless we recursively apply readonly transformations.

## PART 15 -- const vs readonly

### 44. Difference?
**Answer**: const applies to a variable binding, while readonly applies to a property or type member. const prevents reassignement of the variable, whereas readonly prevents assingment to that property through the type system.

## PART 16 -- Enums

### 45. What is an enum?
**Answer**: An enum allows us to define a named set of related constants. TypeScript supports numeric and string enums, although in many modern codebases I prefer string literal unions when I only need a compile-time set of allowed values.

```ts
enum Status {
    Active = "active",
    Inactive = "inactive",
}
```
Alternative:
```ts
type Status = "active" | "inactive";
```

**Cross-question**

#### i) Why might you prefer a union over an enum?
**Answer**:
A string literal union is simpler when I only need type-level restrictions, and it doesn't introduce an enum runtime object. The choice depends on whether I need runtime enum behavior.

## PART 17 -- TypeScript + React

### 46. How do you type React component props?
**Answer**: 
```ts
interface ButtonProps {
    title: string;
    disabled?: boolean;
}
```

I define an explicit props contract using an interface or type alias and use it as the component's props type. I keep the props specific to what the component actually needs rather than making everything optional.

### 47. How do you type useState?
**Answer**: 
```ts
const [user, setUser] = useState<User | null>(null);
```
When the initial value doesn't provide enough information for TypeScript to infer the eventual state type, I provide the generic explicitly. For example, if a user starts as null and is populated later, I use User | null.

**Cross-question**

#### i) Why not just useState(null)?
**Answer**: Because TypeScript may infer the state too narrowly from the initial null, which won't correctly represent the state after a user is loaded.

### 48. How do you type useRef?
**Answer**: 
```ts
const inputRef = useRef<HTMLInputElement | null>(null);
```

I specify the element or value type that the ref will point to, and I include null because the ref may not be initialized initially.

### 49. How do you type React events?
**Answer**: 
```ts
const handleChange = (
    event: React.ChangeEvent<HTMLInputElement>
) => {
    console.log(event.target.value);
};
```

I use React's event types based on the element and event being handled, such as ChangeEvent<HTMLInputElement> for an input change event.

### 50. How do you create a generic React component?
**Answer**:
```ts
interface SalectProps<T> {
    options: T[];
    getLabel: (option: T) => string;
    onChange: (option: T) => void;
}
```
For reusable compoents that can work with different data types, I can make the component generic. This allows the component to preserve the type of the data while keeping the component reusable.

## PART 18 -- TypeScript + Backend ? NestJS

### 51. Why does NestJS commonly use classes for DTOs instead of interfaces?
**Answer**: Interfaces only exist at compile tile and are erased from the generated JavaScript. nestJS uses runtime metadata and decorators for features such as validation and transformation, so classes are useful because they exist at runtime and can carry decorators and metadata.

For example: 
```ts
class CreateUserDit {
    name: string;
    email: string;
}
```
can be decorated

### 52. Interface vs DTO?
**Answer**: An interface is primarily a compile-time type contract, while a DTO is an application-level object used to define the shape of data crossing a boundary, such as an HTTP request. In NestJS, DTOs are commonly implemented as classes because runtime decorators can be attached to them for validation and transformation.

### 53. Does TypeScript validate incoming API requests?
**Answer**: No, TypeScript's types don't exist at runtime, so they don't validate HTTP input. Runtime validation needs to be implemented separately, for example though NestJS validation pipes and class-validator, or through another runtime schema validation library.

## PART 19 -- Advanced Real-World Questions

### 54. Should frontend and backend share TypeScript types?
**Answer**: It depends on the architecture. Sharing types can reduce duplication and keep contracts consistent, especially in a monorepo, but I wouldn't automatically share every backend type with the frontend. Sharing too much can create tight coupling between applications. I prefer sharing stable API contracts or explicitly desinged contract packages rather than exposing internal domain models.

### 55. What are the disadvantages of sharing types across frontend and backend?
**Answer**: 
The biggest risk is coupling. A backend implementation change can uninterntionally force frontend changes even when the API contrct hasn't changed. It can also expose internal domain concepts to clients. So I'd distinguish between shared API contracts and internal implementation types.

### 56. Where should types live in a large application?
**Answer**: 
I avoid putting every type into one global types folder. Types should generally live close to the domain or feature that owns them. Shared types that genuinely cross application or feature boundaries can live in a shared package. The goal is to make ownership and dependencies clear rather than creating a dumping ground for types.

### 57. How do you avoid overusing TypeScript?
**Answer**: I use TypeScript when it provides meaningful contracts and prevents errors, but I avoid creating unnecessarily complex types just to make the compiler happy. If a type becomes harder to understand than the code it protects, I'd reconsider the desing. The goal is maintainability, not maximum type-level complexity.

### 58. What is the difference between compile-time and runtime?
**Answer**: Compile-time is when TypeScript analyzes the source code and checks types before execution. Runtime is when the generated javaScript actually executes. TypeScript can catch many errors at compile time, but runtime data still needs runtime handling and validation.

### 59. Can TypeScript guarantee an API response is correct?
**Answer**: 
No. TypeScript can describe what we expect the API response to look like, but it can't guarantee that an external system actually returns that shape. For untrusted external data, runtime validation is required if correctness of the shapre is important.

### 60. What is the biggest mistake developers make with TypeScript?
**Answer**:
One common mistake is treating TypeScript's compile-time types as runtime validation. Another is overusing any or building unnecessarily complicated types. TypeScript works best when it clearly expresses domain contracts without becoming a second programming language that is harder to maintain than the application itself.

