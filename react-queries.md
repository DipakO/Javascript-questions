

\**\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\**\*\* React *\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\**\*\*

1\. What is the diff between real DOM and virtual DOM ?

Ans: The Real DOM is Actual DOM (Document Object Model) that maintained by Browser, Every HTML element is represented as node, and JavaScript can directly

manipulate these nodes. Directly update to it can be expensive because they may trigger layout and repaint operations.

The Virtual DOM is a lightweight copy of Real DOM that maintained by React. When the application state changes, React update the virtual DOM first, Compare

it with the previous version. (a process called diffing), and update only changed part of real DOM.

Browser creates the real DOM after loading HTML page.

I) Why Is Virtual DOM faster ?

Ans: Virtual DOM is not always faster, but that reduces unnecessary Real DOM operations.

Interview Cross Questions:

Q1. Is Virtual DOM part of JavaScript ?

Ans: No, Virtual DOM is not part of JavaScript. It is an implementation used by libraries like React.

Q2. Who creates the Real DOM ?

Ans: The browser creates the Real DOM after parsing the HTML.

Q3. Who creates the Virtual DOM ?

Ans: React create and managed virtual DOM

Q4: Does React update the Real DOM directly ?

Ans: No, React first update virtual DOM, compare it with previous version, and then applies only the necessary changes to real DOM.

Q5. What is the Diffing ?

Ans: Diffing is the process of comparing the old virtual DOM with new virtual DOM to determine what has changed.

Q6. What is the Reconciliation ?

Ans: Reconciliation is the overall process React uses to update the UI. It includes diffing the Virtual DOM and applying the minimal required updates to the 

real DOM.

Q7. Why is the Real DOM considered expensive ?

Ans: Because changes to the Real DOM may trigger layout calculations, repainting, and rendering, which are more costly than JavaScript objects.

Q8. Does React update whole page when state change ?

Ans: No. React updates only the parts of the Real DOM that have actually changed.

Q9. Can JavaScript manipulate Real DOM without React ?

Ans: yes.



2.) What is the difference between React.memo, useMemo and useCallBack ?

Ans: The key is to understand what each one memorize.

i) React.memo  : (Component) Prevent unnecessary component re-rendering.

ii) useMemo    : (Value) Prevent expensive calculations from running again.

iii) useCallback : (Function) Prevent function recreation on every render.

Think of it this way:

React.memo --> Memorize a Component.

useMemo    --> Memorize a Value.

useCallback--> Memorize a Function.

\*\*\* React.memo:

What is the React.memo ?

Ans: React.memo is a Higher order component that prevent a function component from re-rendering if its props have not changed.

Without React.memo, when a parent component re-renders, all child component also re-render, event if there props are unchanged.

How React.memo works ?

Ans: React perform shallow comparison of the previous props and the new props. 

If they are equal then skip re-rendering Otherwise render again.

When to use React.memo ?

Ans: Child component are expensive to render.

Parent updates frequently.

Child props rarely change.

\*\*\* useMemo

What is useMemo ?

Ans: useMemo memorize the result of calculation.

Instead of recalculating every render, React returns the cached value until one of the dependencies changes

When to use useMemo ?

Ans: Sorting large array.

Filtering data.

Complex calculations

Heavy computations

\*\*\* useCallback

What is the useCallback

useCallback memorize a function.

Normally every render creates a new function object. Every render create a new function instance

Feature     React.memo    useMemo       useCallback

Memorize    Component   Value       Function

Prevents    Components re-render  Expensive Recalculation   Function recreation

Returns     Component   Any Value     Function

Common use    Child Component   Heavy computations    Event handlers passed as props.

\**\*\**\*\* Common Cross Question.

Q1. What is the memorization ?

Ans: Memorization is an optimization optimization technique where result of a computation is cached and reused instead of recomputing it until its dependencies

change.

Q2. Does React.memo prevent all re-renders ?

Ans: No. It's only skip re-render when the component's props are shallowly equal. It does not stop re-renders caused by the component's own state changes or

context updates.

Q3. Does useMemo improves performance in every case ?

Ans: No. It also has a cost because React must store the cached value and compare dependencies. Use it for expensive computations, Not for simple expression.

Q4. Why do we use useCallback with React.memo ?

Ans: because React.memo compares props by reference. without useCallback, a new function is created on every render, so the memorized child still sees it's

function prop as changed and re-renders.

Q5. Can useCallback replace useMemo ?

Ans: No. useCallback memorizes a function, while useMemo memorizes the result of a computation.

Q6. Can React.memo work without useCallback?

Ans: Yes, but if you're passing functions as props, those functions will usually have new reference on every render. In that case, React.memo won't be able 

to skip the re-render. That's why React.memo and useCallback are often used together. 

Ready Ans \**\*\*\*\*\*\*\*\**\*\*

React.memo memorizes an entire component and skips re-rendering when it's props haven't changed. useMemo memorizes the result of an expensive calculation, so

it isn't recomputed on every render. useCallback memorize a function, keeping the same function reference between renders until dependencies change. They are

often used together: React.memo for child components, useMemo for expensive derived values, and useCallback for callback props passed to memorize children. 







3\) What is the React ?

Ans: React is open-source JavaScript library that developed by Facebook for building interactive and re-usable user interface, specially for single page 

application. React helps us to build web applications by breaking the UI into reusable components. Instead of manually manipulating HTML using JavaScript,

we are simply update the application's state, and React automatically update UI.

Cross Questions

i) Why React is called library instead of framework ?

Ans: React focuses only on building the user interface.

It does not provide the build in solution for:

Routing,

State Management,

HTTP Request,

Form Validation

Developer choose there own libraries.

Angular, on other hand, provide these all feature out of the box, so it is consider as Framework.



ii) What problem does react solve ?

Ans: Before React: 

document.getElementById('name').innerHTML = "John";

Developers manually updated the DOM.

In large applications: 

Difficult to maintain, duplicate code, performance issues, hard to track UI changes.

React Introduced : Component Architecture, Declarative UI, Virtual DOM, Efficient Updates.



iii) What is SPA ?

Ans: SPA Stands for single page application.

Browser loads one HTML page initially.

Later, React updates only the required parts of the page without reloading the entire page.

iv) Is react only for SPA ?

Ans: No, React can be used for: 

Single page application

Multi-page application

Dashboards

Admin Panels

E-commerce Website

Mobile application using React Native

4\*\*\*) What are the Advantages of react ?

Ans: It uses a component based architecture, allow us to create reusable and maintainable UI components. 

React uses virtual DOM, which update only the changed elements, improving rendering performance.

React support one way data flow, making state changes predictable and easier to debug.

Cross Questions \**\*\*\*\*\*\*\*\*\*\**\*\*88

i ) What is the Component-Based Architecture ?

Ans: Instead of writing one large HTML page, we divide the UI into smaller reusable components.

5\*\*\*) What is JSX ?

Ans: JSX stands for JavaScript XML. It is a syntax extension for JavaScript that allow us to write HTML-like code inside JavaScript.

During, compilation, Babel converts it into React.createElement() calls, which React uses to crate the virtual DOM.

Cross Questions

i ) Is JSX mandatory ?

Ans: No, React can written without JSX using React.createElement(), but JSX makes code much cleaner and easier to maintain. 

6\*\*\*) Why do we use keys in React Lists ?

Ans: Keys uniquely identify list items so React can efficiently update only the changed element during reconciliation, improving performance and preserving 

component state.

7\*\*\*) What is Reconciliation ?

Ans: Reconciliation is React's process of comparing the old and new Virtual DOM after a state or prop change. Using it's diffing algorithm, React updates only

part of real DOM that have changed, making rendering efficient.

Cross Questions

i ) What is Diffing ?

Ans: Diffing is the algorithm React uses during reconciliation to compare two virtual DOM trees and determine the minimal set of DOM updates.

ii ) What assumptions does React's diffing algorithm make?

Ans: 1. Elements of different types produce different trees.

2\. Developers provide stable key props to identify children lists.

iii ) How do keys help reconciliation?

Ans: Keys allow React to match list items between renders. With stable unique keys, React can identify which items were added, removed, or moved, resulting in

fewer DOM operations and preserving component state.

1\. **\*\*\* React Component \*\*\***

1\*\*\*) Difference between functional and class component ?

Ans: Functional Component are JavaScript Function that return JSX and use Hooks for state and side effects. Class Component use ES6 classes, lifecycle methods,

and this.useState(). Functional Component are preferred in modern React because they are simple, more readable, and align with current React best practices. 

Functional        Class

JavaScript Function     ES6 class

Uses Hooks        Uses Lifecycle Method

No this keyword       Uses this

Less code         More boilerplate

Better readability      More complex

Recommended in modern React   Mainly used in legacy projects

2\*\*\*) Why are Functional Component preferred ? 

Ans: They reduce boilerplate, eliminate the need for this, support Hooks, encourage reusable logic through Custom Hooks, and are the recommended approach for

new React Application.

3\*\*\*) What are Pure Component.

Ans: Pure Component is Class Component that perform a shallow comparison for props and state to skip unnecessary re-rendering. In Functional Components, the 

equivalent optimization is React.Memo.  

Cross Questions:

i ) What is shallow comparison?

Ans: It's compare only first level of values or object references, not deeply nested properties. 

4\*\*\*) Difference between props and state ?

Ans: Props are read-only values that passed from parent component to child component, while state is owned and updated by the component itself. Props enable 

communication between components, whereas state manage dynamic data within the component.

3\. **\*\*\* React Hooks \*\*\***

1\*\*\*) What are Hooks?

Ans: Hooks are special function that introduce in React 16.8 that allow function component to use React features such as state, lifecycle method, refs without

writing class component.

Before Hooks these feature are only available in Class Components. Hooks make code simple, reusable , and easier to maintain.

2\*\*\*) useState ?

Ans: useState is a Hook that adds state to Functional Components. It's return the current state value and setter function. Calling the setter schedules a 

re-render with updated state.



Cross Question 

Q1 ) How does useState work ?

Ans: When a component renders for the first time, React stores the initial state internally.

On subsequent renders, React return current stored state instead of reinitializing it.

When the setter function is called, React updates the stored state, schedule a re-render, and the component receives the latest state value on the next render.

Q2 ) Why is state update asynchronous?

Ans: React schedules and batches state updates to improve performance by reducing unnecessary re-renders. Because of this, the updated value is available on

the next render rather than immediately after calling the setter.

Q3) Why shouldn't state be modified directly?

Ans: React relies on immutable update to detect changes. Directly mutating state can prevent React from recognizing updates, resulting in stale UI and 

rendering bugs.

3\*\*\*) useEffect ?

Ans: useEffect is used for side effects such as API calls, subscriptions, timers, and event listeners. It runs after React updates the DOM, and its execution

depend on the dependency array.

Cross Question.

Q1) What is a Cleanup Function?

Ans: Cleanup Function is returned from useEffect and is executed before the effect runs again and when the component unmounts. It is used to clean up resources

like event listeners, timers, or socket subscriptions.

Q2) When is cleanup executed?

Ans: Before the effect runs again (If dependency changed)

When the component unmounts 

Q3) Why cleanup important ?

Ans: To prevent: Memory leak, duplicate event listener, unnecessary API polling, stale subscriptions.

4\*\*\*) What is useRef ?

Ans: useRef stores a mutable value or DOM reference that persists across renders without causing a re-render when updated.

Cross Question:

Q1) Why use useRef ?

Ans: Access DOM element, Focus an input, Store previous values, Store interval or timeout IDs, Keep mutable values between renders without triggering a 

re-render.

Q3) Difference Between useRef and useState

Ans: useState manages data that affects the UI and triggers re-renders when updated. 

useRef stores mutable values that persist across renders but do not trigger re-renders.

useState        useRef

Trigger re-render       No re-render

Stores UI state       Stores mutable values or DOM references 

Uses setter function      Update ref.current directly 

Causes component update     Does not cause component update.

5\*\*\*) Custom Hooks:

Ans: Custom Hook is a reusable function that starts with use and encapsulates shared stateful logic using React Hooks. It improves code reuse while keeping

each component's state independent. 

Cross Question

Q1. Why should the function name start with use?

Ans: React relies on this naming convention so linting tools can enforce the Rules of Hooks and developer can easily recognize Custom Hooks.

4\. **\*\*\* React Rendering \*\*\***

1\*\*\*) What is Rendering in React ?

Ans: Rendering in React is process of executing a component function to generate a React element tree. React then compare this new Virtual DOM with the 

previous one using reconciliation process and updates only the necessary parts of real DOM.

It's important to understand that a component re-rendering does not necessarily mean the real DOM is updated. React first perform reconciliation and only if 

its find difference does it updates the real DOM.

5\. **\*\*\* React Lifecycle \*\*\***

1\*\*\*) What is the React Component Lifecycle ?

Ans: The React Component Lifecycle describe the different phases a component goes through from creation to removal.

In Class Components, this phases are handled using lifecycle methods such as componentDidMount, componentDidUpdate, and componentWillUnmount.

In Functional Components, we achieve the same behaviour using the useEffect hook with different dependency arrays and cleanup Functions.

2\*\*\*) componentDidMount (Using Hook)

Ans: componentDidMount is called only once after a component is mounted to the DOM.

3\*\*\*) componentDidUpdate (Using Hook)

Ans: componentDidUpdate runs after a component updates due to changes in state or props.

4\*\*\*) componentWillUnmount (Using Hook)

Ans: componentWillUnmount executes just before a component is removed from the DOM.

Cross Questions

Q1. When is cleanup executed?

Ans: Before the component Unmount. 2. Before the effect runs again when dependencies change.

Q2. Can useEffect replace all lifecycle methods ?

Ans: There are lifecycle methods like getSnapShotBeforeUpdate and shouldComponentUpdate that don't have direct hook equivalents. Similar behaviour is achieved

with other React APIs such as React.memo, useLayoutEffect. depending on use cases.

Q3. Diff between useEffect and useLayoutEffect ?

Ans: 

useEffect           useLayoutEffect

Runs after the browser paints the screen    Runs synchronously after the DOM updates but before the browser paints.

Doesn't block painting          Blocks painting until it finishes.

Used for API calls, subscriptions, timers     Used for DOM measurements or preventing visual flicker.

useEffect runs after browser has painted the updated UI, making it suitable for most side effects such as API calls, subscriptions or timers.

useLayoutEffect run synchronously after React Updates the DOM but before the browser paints the screen. It's mainly used when you need to measure or modify

the DOM before the user sees it, such as calculating element sizes or adjusting scroll positions.

6\. **\*\*\* State Management \*\*\***

1\*\*\*) What is the state management ?

Ans: State management is process of storing, updating, and sharing data across different component in application.

React provide local state using useState, but as application grow, multiple component often need access to the same data, such as user information, 

authentication status or application setting.

To avoid problem like prop drilling and to centralize shared data, we use state management solutions such as context API, Redux Toolkit, Zustand, or MobX.

Types of state

Type          Exm.

Local state         Input field, Modal Open/Close

Global State        Logged-in user, Theme, Cart

Server State        API Data.

2\*\*\*) What is Context API ?

Ans: Context API is React's in-build mechanism for sharing values across components without prop drilling. It's best suited for relatively stable global

data such as authentication, theme, or language preference.

Context itself is not a complete state management library. It only provides way to pass values through the component tree.

Advantages: Built into React, No Extra Library, Eliminates Props Drilling, Easy to use.

Limitations: Frequent update can cause many components to re-render.

Lacks built-in middleware and developer tools

Less suitable for large, complex application.

Cross Questions

Q1. Does Context replace Redux?

Ans: No, Context solves props drilling, while Redux provides a structured approach for managing complex global state with predictable updates and powerful

tooling.

3\*\*\*) Redux ?

Ans: Redux is predictable state management library that stores global state in a centralize store.

Component Dispatch actions, reducers update the state, and subscribed components receive the updated values.

Core Concepts

Store: Stores the application's state.

Action: Describes what happened.

Reducer: Updates state based on the action.

4\*\*\*) Redux Toolkit (RTK)

Ans: React Toolkit is official way to write Redux application. It simplifies Redux by reducing boilerplate, provide utilities like createSlice and 

configureStore, and handling immutable updates internally with Immer.

Benefits: Less boilerplate, Easier Setup, Better readability, Built-in Immer, Recommended by Redux maintainers. 

Cross Questions

Q1. Why Redux Toolkit instead of Redux ?

Ans: Because it's reduce boilerplate, simplifies configuration, and it's officially recommended approach.

Q2. What is the creatSlice ?

Ans: It automatically generates: Reducers, Action creators, Action types. From a single definition.

Q3. What is the configureStore? 

Ans: It creates the Redux store with sensible defaults, including good middleware and DevTools support.

5\*\*\*) Zustand

Ans: Zustand is a lightweight state management library for React.

It provide simple API using Hooks and does not requires reducers, actions, or providers.

Zustand is easier to learn that Redux and is the well suited for small to medium sized application or projects

 that need global state without Redux's complexity.

Advantage: Minimal boilerplate, No Providers Required, Fast, Hook based API, Easy to use.

Cross Questions

Q1. Is Zustand faster than Redux?

Ans: It can have less overhead for many use cases because components subscribe only to the parts of state they use. 

The right choice depends on the application's requirement.

6\*\*\*) MobX

Ans: MobX is state management library based on observable.

Instead of dispatching actions and writing reducers, MobX automatically track which 

observable state a component uses and re-render only those components when the state changes.

Advantage: Less Boilerplate, Automatic reactivity, Easy to update state, Good performance. 

Limitations: Different mental model, Less common in modern React project than Redux Toolkit and Zustand.

7\*\*\*) Context API vs Redux Toolkit

Ans: Context API is primarily for avoid prop drilling and sharing simple global values.

Redux Toolkit is a full-featured state management solution with a centralized store, predictable updates,

middleware, and excellent debugging support, making it better suitable for large and complex application.

7\. **\*\*\* Redux Interview Questions \*\*\***

1\*\*\*) What is Store?

Ans: The store is central object in Redux that holds the application's global state.

There is a typically single store for the application. Component reads state from the store and dispatch

the action to update it.

Cross Questions

Q1. Can Redux have multiple stores?

Ans: Technically yes, but generally it's bad way.

Q2. Who update the store ? 

Ans: Reducers update the store after processing dispatch actions. 

2\*\*\*) What is the Action ?

Ans: Action is plain JavaScript object that describes what happened in the application.

Every action must have a type property. It can also include additional data, usually called payload.

Cross Questions

Q1. Can Action update state ?

Ans: No, Action only describe what happened. Reducers actually update the state.

Q2. Why does every action need type ?

Ans: Because reducer use the action type to determine how the state should change.

3\*\*\*) What is the Reducers ?

Ans: Reducer is pure function that receives current state and an action, then returns 

a new state based on action.

Reducers should not mutate the existing state. Instead, they return a new state object.

Cross Questions

Q1. Why is reducers called pure function ?

Ans: Because: Same Input --> Same Output

No API Calls, No Timers, No DOM manipulation, No side effects

4\*\*\*) What is Dispatch?

Ans: Dispatch is method used to send an action to the Redux store.

When dispatch() is called, Redux sends the action through middleware, then to reducers, which update the store.

Cross Questions

Q1. Does dispatch update state directly?

Ans: No, dispatch sends an action. Reducer update the state.

5\*\*\*) What is Middleware ?

Ans: Middleware sits between dispatch() and the reducer.

It intercepts dispatched actions and allows us to perform additional logic such as logging, API calls,

authentication checks, or asynchronous operations before the action reaches the reducer

Cross Questions

Q1. Why do we need middleware ?

Ans: Because reducer must remain pure and should not contain side effects.

Q2. Name some Redux middleware.

Ans: Redux Thunk, Redux Saga, Redux Logger.

6\*\*\*) What is the Redux Thunk ?

Ans: Redux Thunk is middleware that allows action creators to return a function instead of a plain action object.

This function receives dispatch  and getState, enabling asynchronous operations such as API calls before 

dispatching regular action.

Cross Questions

Q1. Why can't reducer perform API calls?

Ans: Because reducer must remain pure and synchronous. 

Q2. What does Thunk receive ?

Ans: (dispatch, getState)

7\*\*\*) What is RTK Query?

Ans: RTK Query is data fetching and caching solution built into Redux Toolkit.

It simplifies API calls by automatically handling data fetching, caching, loading states, error states, cache invalidation,

and re-fetching.

It eliminates much of the boilerplate traditionally required with Redux Thunk for server side data.

Advantages: Automatic caching, Automatic loading state, Automatic error handling, Cache invalidation, Less boilerplate, 

Background re-fetching.

Cross Question:

Q1. Does RTK Query replace Redux Thunk ?

Ans: For most API data fetching, yes. RTK Query is the recommended choice because it provides built-in caching and 

request management. Redux Thunk is still useful for other asynchronous business logic that isn't centered around 

fetching server data.

8\. **\*\*\* React Forms \*\*\***

1\*\*\*) What are the Forms in React ?

Ans: Forms in React are used to collect user input such as login credentials, registration details, search query,

or contact information.

React provides two approaches for handling forms:

1\. Controlled Components.

2\. Uncontrolled Components

In modern react applications, Controlled Component are more common because they provide better control over form

data and validation.

2\*\*\*) What are Controlled Components?

Ans: Controlled Component is a form element whose value is controlled by React state. The input value is stored in 

state using useState, and every change updates the state through an onChange handler.

Since React owns the form data, it becomes easier to validate, reset, and manipulate the form.

Advantage: Easy Validation, Easy error handling, Easy reset, Predictable state, Better Debugging.

Cross Questions

Q1. Why are Controlled Components preferred?

Answer: Because react always knows the latest form values, making validation, conditional rendering, and 

form submission much easier.

3\*\*\*) What are Uncontrolled Components?

Ans: Uncontrolled Components store its value inside the DOM instead of React state.

React accesses the input value using a ref when needed.

Since React doesn't manage the value of every keystroke, uncontrolled components generally trigger fewer re-renders.

Advantage: Simpler for very basic forms, Fewer re-renders, Easy integration with non-React code.

Limitation: Harder validation, Less Control, More difficult to manage complex forms.

4\*\*\*). Difference Between Controlled and Uncontrolled Components

Controlled        Uncontrolled 

React controls data       DOM controls data

Uses useState       Uses useRef

Re-render on input changes    No re-render on every keystroke

Easier Validation       Harder Validation

Recommended for most forms    Better for simple forms or file inputs

5\*\*\*) Form Validation

Form Validation insure that user input meets bussiness and data requirement before submission.

Validation can occur: On every input change

On blur (when leaving a field)

On form submission

Common validation rules include required fields, email format, password lenght, minimun and maximum values, 

and custom business rules.

Cross Questions

Q1. Client-side vs Server-side validation ?

Ans: Client side validation improves user experience by catching obvious error early, but server-side validation 

is still required because client-side checks can be bypassed.

Q2. Why is server-side validation still necessary ?

Ans: Because users can modify requests or bypass client-side validation, so the server mush always validate incoming data.

6\*\*\*) React Hook Form ?

Ans: React form hook is a lightweight library for handling forms in React.

It uses uncontrolled inputs internally with refs, which significantly reduces unnecessary re-renders compared to 

traditional controlled forms.

It provides built-in validation, error handling, form state management, and integrates easily with schema validation

library such as Yup and Zod.

Advantages: Very few re-renders, Built-in validation, Smaller bundle size,  Easy integration with Yup and Zod.

Better performance for large forms.

Cross Questions

Q1. Why is React Hook Form faster?

Answer: Because it primarily uses uncontrolled inputs with refs instead of updating React state on every keystroke, 

Resulting in fewer component re-renders.

Q2. Can React Hook Form validate forms?

Ans: Yes, It supports: Required, Min/Max length, Pattern matching, Custom validation, Yup, Zod.

Frequently Asked Scenario

Interviewer

Why would you choose React Hook Form instead of useState?

Ans: For small form with just some fields, useState is perfectly fine and keeps the implementation straightforward

For large forms, I prefer React Hook Form because it minimize unnecessary re-renders, provides built-in validation, 

simplifies form state management, and integrates well with validation libraries like Yup and Zod. This results in 

better performance and cleaner, more maintainable code.

9\. **\*\*\* React Performance Optimization \*\*\***

1\*\*\*) What is the performance optimization in React ?

Ans: Performance optimization in React means improving an application's speed, responsiveness, and resource usage by

 reducing unnecessary rendering, minimizing bundle size, and loading only the required resources.

Common optimization technique:

Lazy loading, Code Splitting, React.lazy, Suspense, Memorization, Image Optimization, Bundle Optimization.

2\*\*\*) Lazy Loading?

Ans: Lazy loading is technique where components or resources are loaded only when they are needed instead of 

loading everything during the initial page load.

This reduces the application's initial bundle size and improve first page load performance. 

Advantages: Smaller initial bundle, Faster first load, Better user experience, Less memory usage.

Cross Questions

Q1. Does lazy loading improve SEO?

Ans: For client-side rendered React applications, lazy loading primarily improves performance.

SEO depends on the rendering strategy (CSR vs SSR/SSG). In frameworks like Next.js, SSR, and SSG provide better SEO.

Q2. When should we use Lazy Loading?

Ans: Large pages, Dashboards, Admin panels, Heavy components, Feature modules, Route-based loading

3\*\*\*) Code splitting ?

Ans: Code splitting is process of dividing a large JavaScript bundle into smaller chunks that can be loaded on 

Demand.

Instead of downloading the entire application at once, React downloads only the required code for the current

page or feature.

Cross Questions

Q1. Difference between Lazy Loading and Code Splitting?

Ans: Code splitting is process of breaking code into multiple bundles.

Lazy Loading is the technique of loading those bundles only when needed.

Q2. Which React feature enables code splitting ?

Ans: Dynamic import() together with React.lazy.

4\*\*\*) React.lazy?

Ans: React.lazy is a React API used to dynamically import components. 

Instead of including a component in the initial bundle, React downloads it only when it rendered. 

Cross Questions

Q1. Can React.lazy load named exports?

Ans: Not directly, React.lazy expects a module with a default export. For named exports, you need 

to map them to a default export during the dynamic import.

Q2. Does React.lazy work without Suspense?

Ans: No, Lazy-loaded component must be wrapped in \<Suspense>

5\*\*\*) Suspense ?

Ans: Suspense is React component used to display fallback content while waiting for a lazy-loaded 

component to finish loading.

It provides a better user experience by showing loading indicators instead of a blank screen.

Cross Questions

Q1. Why Suspense is required ? 

Ans: Because Lazy-loaded components are downloaded asynchronously, React needs fallback UI while waiting.

6\*\*\*) Image Optimization

Ans: Image Optimization improves application performance by reducing image size, loading images efficiently, and 

serving the appropriate image for each device.

Common technique :

Compressing Images, Using modern formats like WebP or AVIF, Lazy loading images, Serving responsive image sizes, 

Using optimized image components (Such as Next.js Image)

Benefits: Faster loading, Less bandwidth usage, Better Core Web Vitals, Improved user experience.

Cross Questions

Q1. Why use WebP?

Ans: Because it generally provides much smaller file sizes than JPEG or PNG while maintaining similar visual quality.

Q2. Why should not we load full size images ?

Ans: They increase bandwidth usage and slow down page loading.

7\*\*\*) Bundle Optimization.

Bundle optimization reduces the size of JavaScript, CSS, and other assets downloaded by the browser.

A Smaller bundle improves initial page load time and overall application performance.

Common techniques.

Code splitting, Lazy loading, Tree Shaking, Removing unused dependencies, Dynamic imports, Minification, Compression, 

Image Optimization.

Cross Questions

Q1. What is Tree Shaking?

Ans: Tree Shaking removes unused JavaScript code during the production build, reducing bundle size.

Q2. What tools can analyze build size?

Ans: Webpack Bundle Analyzer and similar tools provided by modern build system like Vite or Next.js integrations.

Frequently Asked Scenario

Interviewer

Your React application loads slowly. What optimizations would you perform?

Ans: I would first analyze the application's bundle to identify large dependencies. Then I'd implement route-based

code splitting and lazy loading for heavy modules, optimize images using modern formats and responsive sizing, remove unused

dependencies, enable tree shaking, and memorize expensive components where appropriate. I'd also review unnecessary re-renders

using React DevTools Profiler and ensure only the required data and assets are loaded initially.

Q1. What is Tree Shaking?

Ans: Remove unused code from the production bundle.

10\. **\*\*\* React Error Handling \*\*\***

1\*\*\*) What is error handling in React ?

Ans: Error handling in the React is the process of detecting, managing and covering from error so that the application 

remains stable instead of crashing completely.

React application can encounter different types of errors, like

Rendering Errors, JavaScript runtime errors, API errors, Network failures, Asynchronous errors.

React provides Error Boundaries for UI rendering errors, while JavaScript's try...catch and async error handling are used 

for synchronous and asynchronous operations.

2\*\*\*) What is an Error Boundary ?

Ans: Error boundary is React Component that catches rendering errors in its child components and displays a fallback UI 

instead of allowing the entire application to crash.

Advantages: Prevent entire application crash, Displays fallback UI, Logs errors, Improves user experience.

Q1. Can Functional Components be Error Boundaries?

Ans: Not directly, React currently requires class Component to implement an Error Boundary.

3\*\*\*) What Errors Do Error Boundaries Catch?

Ans: It catches errors during rendering, lifecycle methods, and constructors of child components. It does not catch API 

errors, event handler errors, or other asynchronous errors.

4\*\*\*) What is Try...Catch?

Ans: try...catch is JavaScript's built-in error handling mechanism for synchronous code. It is also commonly used with

 async/await to handle asynchronous error.

Cross Questions

Q1. Does try...catch catch async errors automatically?

Ans: No, For async functions, use await inside try block or handle rejected Promises with .catch().

5\*\*\*) Async Error Handling

Asynchronous operation such as API calls can fail due to network issues, server errors, on invalid responses.

We handle these errors using try...catch with async/await or by attaching a .catch() handler to Promises.

Cross Questions

Q1. Why use try...catch with async/await?

Ans: Because it makes asynchronous error handling easier to read and maintain compared to chaining multiple 

.then() and .catch() calls.

Q2. What if we don't catch API errors?

Ans: The promise rejection can go unhandled, leading to console errors and poor user experience.

6\*\*\*) Common Error Handling Strategies

In production applications, I usually follow these practices:

Use Error Boundaries for rendering errors.

Use try...catch for synchronous operations.

Use try...catch with async/await for API calls.

Display user-friendly error messages instead of raw exceptions.

Log error to monitoring tool such as Sentry or similar services.

Provide retry options for recoverable failures.

Error Boundary vs Try...Catch

Error Boundary          Try...Catch

React feature         JavaScript feature

Catches rendering error       Catches synchronous exceptions

Shows fallback UI       Handles code exceptions errors

Cannot catch API errors       Can handle API calls with async/await

Class Component implementation      Works in any JavaScript code.

Error boundary protect the React UI from rendering errors by showing fallback content, while try...catch handles

JavaScript expressions and asynchronous operations such as API calls. They solve different problems and are often

 used together in a production React application.

Async/Await vs Promise.catch()

async/await         Promise.catch()

Cleaner syntax          Chained syntax

Uses try...catch        Uses .catch()

Easier to read          Fine for simple chains 

Preferred in modern React       Still valid

Frequently Asked Scenario

FQ1. If your API fails, how will you handle it?

Ans: I use try...catch around asynchronous API calls, show a meaningful error message to the user, log the error for

 debugging, and provide a retry mechanism when appropriate 

FAQ2. What is componentDidCatch() ?

Ans: It is an error boundary lifecycle method used to log error details after a rendering error has been caught.

FAQ3. What is getDerivedStateFromError() ?

Ans: It updates the component's state so that fallback UI can be rendered after an error occurs.

FAQ4. Where should Error Boundaries be placed?

Ans: Around routes, Around feature modules, Around Dashboards, Around third party widget.

11\. **\*\*\* API Calls in React \*\*\***

1\*\*\*) What is an API calls?

Ans: API call is a request from frontend to a backend server to retrieve or modify data. In React, API calls are commonly made with Fetch or Axios inside

useEffect or event handlers.

2\*\*\*) Fetch vs Axios

Both are used to make HTTP requests. Fetch is a built into modern browsers and is suitable for many use cases, but it requires manual JSON parsing and

checking reponse.ok . Axios is third party library that automatically parses JSON, rejects non-2xx responses, supports interceptors, and simplifies request

configuration.

Comparison Table

Fetch             Axios

Built in browser        External Library

No installation         Installation Required

Manual response.json()        Automatically parses JSON

Doesn't reject on Http 404/500 automatically  Reject Promise for non-2xx responses

Supports AbortController      Support request cancellation

Smaller bundle          Slightly larger bundle

Cross Questions

Q1. Why does Axios feel easier?

Ans: Because, Automatically parsed JSON, Reject non-2xx responses, Supports interceptors, Has cleaner configuration for many projects

3\*\*\*) Promises 

Promise is represents the eventual result of an asynchronous operation. It has three states: Pending, Fulfilled, Rejected.

Cross Questions: 

Q1. Can a fulfilled Promise become rejected?

Ans: No, Promise settles only once.

4\*\*\*) async/await

async/await is a cleaner syntax built on top of Promises. that makes asynchronous code look and behave more like synchronous code. It improves readability

and makes error handling easier using try...catch.

Cross Questions

Q1. Does await block JavaScript?

Ans: No, It pauses only the execution of the current async function. The JavaScript event loop continues processing other tasks.

Q2. Is async/await faster than Promises?

Ans: No, It's syntactic sugar over Promises. The performance is generally comparable; the main advantage is readability.

Promise vs async/await

Promise           async/await

Uses .then()          Uses await

Can become deeply nested      Cleaner and easier to read

Uses .catch()         Uses try...catch

Older syntax          Modern preferred syntax

5\*\*\*) AbortController

AbortController is used to cancel in-progress requests, especially when a component unmounted or a request is no longer needed. It's commonly used with

Fetch and is also supported by modern Axios versions.

Cross Questions:

Q1. Why use AbortController?

Ans: To, Cancel unnecessary requests, Prevent state updates after unmount, Reduce wasted network work, Improve use experience.

Q2. Does AbortController work with Fetch?

Ans: Yes, It is a standard cancellation mechanism for the fetch API.

Q3. Can Axios cancel requests?

Ans: Yes, Modern version of Axios support cancellation using AbortController as well.

Q4. Error Handling During API Calls

Ans: Every call should handle: Loading state, Success State, Error state, Cleanup or cancellation when appropriate.

Frequently Asked Scenario

FAQ1. What happens if the user leaves the page while an API call is still running?

Ans: If the request is no longer needed, I cancel it using AbortController in the useEffect cleanup function. This prevent unnecessary network activity and

avoids updating component state after it has been unmounted.

FAQ2. Can we make multiple API calls simultaneously?

Ans: Yes using Promise.all

FAQ3. What is Promise.all()?

Ans: It runs multiple Promises in parallel and resolves when all of them succeed. If any Promise reject, Promise.all rejects.

FAQ4. Difference between Promise.all() and Promise.allSettled()?

Promise.all         Promise.allSettled

Rejects if any Promise fails      Waits for all Promises to settle.

Best when all requests are required     Best when partial results are acceptable

FAQ5. Why should we avoid API calls inside render?

Ans: Because rendering should be pure. Triggering API calls during render can cause repeated requests and unpredictable behaviour.

FAQ6. How do you fetch data when a page loads?

Ans: I typically use useEffect with an empty dependency array so that data is fetched after the component mounts. Inside the effect, I use async/await with

try...catch for error handling, maintain error and loading states, and use an AbortController in the cleanup function it the request should be cancelled when

the component unmounts.

12\. **\*\*\* React Routing \*\*\***

1\*\*\*) What is React Router?

Ans: React Router is the standard routing library for React applications. It enabled client-side navigation, allowing users to move between different pages

without reloading the entire browser. 

Instead of requesting new HTML page from the server, React Router updates the URL and renders the appropriate React component, providing a faster and smoother

user experience. 

Cross Questions: 

Q1. What is client-side Routing ?

Ans: Client-side routing means navigation happens inside the browser using JavaScript without requesting a new HTML page from server.

Q2. Difference between SPA and MPA?

SPA (Single page application )      MPA (Multi page application )

One HTML page         Multiple HTML pages

Faster Navigation       Full page reload

React Router          Server-side routing

Better user experience        Slower navigation

Q3. Why use React Router?

Ans: Faster Navigation, No full page reload, Better user experience, URL management, Route protection.

2\*\*\*) BrowserRouter

Ans: BrowserRouter is the router implementation provided by React router that uses the HTML5 History API to keep the UI synchronized with browser URL.

It wraps the entire React application and enables routing functionality. All routes are managed inside a single BrowserRouter.

Cross Questions

Q1. Why do we wrap the app with BrowserRouter?

Ans: Because it provides routing context so all routing components (Routes, Route, Link, Navigate) can access navigation information.

Q2. What does BrowserRouter use internally?

Ans: It uses the browsers History API (pushState, replaceState) 

3\*\*\*) Routes

The Route component contains all the application's route definitions. It checks the current URL and renders the first matching route.

Cross Questions

Q1. What replaced \<Switch>?

Ans: Routes , React Router v6 replaced switch with Routes.

4\*\*\*)  Navigate

Navigate is react router component used for declarative navigation or redirection. It commonly used for authentication and protected routes.

Cross Questions

Q1. When should we use Navigate?

Ans: Redirect after login, Protected Routes, Redirect after logout, Invalid routes.

Q2. What replaced Redirect?

Ans: Navigate, 

5\*\*\*) useNavigate

useNavigate is a hook used for programmatic navigation. It allow navigation after performing an action such as form submission, login, or API success.

Cross Questions

Q1. Difference between Navigate and useNavigate?

Navigate        useNavigate

Component         Hook

Declarative navigation      Programmatic navigation

Used in JSX       Used inside functions/ events

Q2. Can navigate go back?

Ans: Yes, with navigate(-1) Moves back one page

Q3. Can navigate replace history?

Ans: Yes, navigate('/login', {replace: true}) This replaces the current history entry instead of adding a new one.  

6\*\*\*) Route Parameters

Route parameters are dynamic values passed through the URL. They are commonly used to identify a specific resource, such as a user ID or product ID.

Route Parameters vs Query Parameters

Route Parameters      Query Parameters

/users/10       /users?id=10

uses useParams()      Uses useSearchParams()

Identifies a specific resource    Used for filtering, sorting, pagination.

BrowserRouter vs HashRouter

BrowserRouter           HashRouter

Uses History API        Uses URL hash (#)

Cleaner URLs          URLs contain #

Preferred for modern application    Useful on static hosting without server configuration

Frequently Asked Scenario

FAQ1. How do you protect routes?

Ans: By checking whether the user is authenticated before rendering the page.

13\. **\*\*\* React Testing \*\*\***

1\*\*\*). What is testing in React ?

ANs: Testing is the process of verifying that React components and application logic work correctly.

It helps identify bugs early, ensure new changes don't break existing functionality, and increase confidence when deploying applications.

The two most commonly used tools are:

"Jest - Test Runner and Assertion Library", "React testing library- Library for testing React components by simulating user interaction"

Cross Questions

Q1. Why do we write tests?

Ans: Detect bugs earlier, Prevent regression, Improve code quality, Enable safe refactoring, Increase confidence before deployment.

Q2. What types of testing exist?

Ans: Unit testing, Integration Testing, End-to-End Testing.

2\*\*\*) What is Jest?

Ans: Jest is JavaScript testing framework used to run tests, make assertions, create mocks, measure code coverage, and verify that application logic behaves

as expected.

Features: Test Runner, Assertion, Mock Functions, Snapshot Testing, Code coverage.

Cross Questions: 

Q1. What is expect()?

Ans: It is an assertion used to verify the expected result.

3\*\*\*) What is React Testing Library (RTL)?

Ans: React Testing Library (RTL) is a library used to test React components by interacting with them the way a real user would.

Instead of testing implementation details, RTL focuses on user-visible behaviour such as rendering, clicking buttons, typing into imputs, and checking

displayed text.

Advantages: Encourage user-centric testing, Less coupled to implementation, Easy to maintain, Works well with Jest.

Cross Questions

Q1. Why use React Testing Library instead of Enzyme?

Ans: React Testing Library encourages testing from the user's perspective rather than inspecting component internals, making tests more reliable and less

brittle.

Q2. What does render() do?

Ans: It renders the component into a virtual DOM for testing.

4\*\*\*) How do you test a React Component?

Ans: I generally follow these steps: 

  1\. "Render the component"

  2\. "Find elements using queries like getByRole or getByText."

  3\. "Simulate user actions such as clicks or typing."

  4\. "Verify the expected UI changes or function calls using assertions."

Jest vs React Testing Library

Jest            React Testing Library

Test runner         Component testing library

Assertion           Renders React Component

Mocking           Simulates user interaction,

Coverage          Queries DOM elements

Unit Testing vs Integration Testing vs E2E Testing

Unit Testing        Integration Testing           E2E Testing

Tests one function/component    Tests multiple component together     Tests complete application

Fast          Medium              Slow

User mocks frequently       Some mocks            Uses real browser

Example: Utility function   Login form with API mock        Login --> Dashboard flow



Frequently Asked Scenario

FAQ1. How would you test a Login component?

Ans: I would render the Login component using React Testing Library, verify that the email, password, and login button are displayed, simulate user input 

using userEvent.type(), click the login button, mock the API response, and then verify that the success message or navigation occurs. I would also test 

validation messages and API failure scenarios.

FAQ2. What is screen?

Ans: screen provided access to the rendered DOM using queries like getByText() and getByRole().

FAQ3. Why is getByRole() recommended?

Ans: Because it closely matches how uses and assistive technologies interact with the page, making tests more accessible and maintainable.

FAQ3. What is userEvent?

Ans: userEvent simulates real user interaction like typing, clicking, selecting options, and tabbing through element.

FAQ4. Difference between fireEvent and userEvent?

Ans: fireEvent          userEvent

Triggers a single event       Simulates realistic user interactions

Lower-level API         Higher-level API

Less realistic          More closely mimics browser behaviour 

FAQ5. What is Code Coverage?

Ans: Code coverage measures how much of your application code is executed during tests. It helps identify untested parts of the application.