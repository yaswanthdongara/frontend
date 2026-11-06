## What Are Libraries?
Libraries are generally more focused on providing solutions to specific tasks, such as manipulating the DOM, handling events, or managing AJAX requests.
An example of a JavaScript library is jQuery.
jQuery became very popular in the early 2010s and was widely used to simplify DOM manipulation, event handling, animations, effects, and more. This library also offered a rich ecosystem of plugins, which made it easy to build common web components like date pickers, sliders, and modal dialogs.
## What Are Frameworks?
Frameworks, on the other hand, provide a more defined structure for building applications. They often come with a set of rules and conventions that developers need to follow.
For example, Angular encourages a component-based architecture with a set of conventions and tools that provide a structured approach to organizing and building applications. Angular gives developers clear guidelines on how to structure components, manage state, handle routing, and interact with services, making it a more opinionated framework.
### In conclusion, libraries and frameworks offer quick solutions to common problems, speed up development, and promote best practices. 
Question: Why was jQuery a popular library of choice in the early 2010s?
jQuery was used to simplify things like DOM manipulation, event handling, animations, and effects.

 Single Page Applications (SPAs) load only one HTML page and dynamically update the content as the user interacts with the app, without reloading the entire page. 
 SPAs heavily use JavaScript to manage the application's state and render content. Instead of requesting new HTML pages from the server, SPAs use JavaScript to manipulate the DOM and fetch data asynchronously. This is often done using libraries and frameworks like React, Vue, or Angular, which provide great tools for building complex user interfaces.
 ### Challenges
 - SPAs have some common issues. One significant issue is that screen readers may struggle with dynamically updated content. When content changes without a page reload, screen readers might not announce these changes, which leaves users unaware of updates to the web app.
 - Another challenge with SPAs is navigation and browser history. 
 - SPAs can pose challenges for SEO. Search engines like Google can have difficulty indexing dynamically loaded content because they may not execute JavaScript properly or may miss content that isn't included in the initial HTML page. This can lead to pages not being indexed correctly.
 - Performance is another consideration. An SPA has to load its JavaScript before it can render anything, so a large bundle leaves the user looking at a blank screen for a longer period of time.

## What Is React, and What Is It Commonly Used For?
React is one of the most popular JavaScript libraries for building user interfaces and web applications. Originally developed at Facebook, now Meta, React has gained huge popularity in web development due to its efficiency, flexibility, and features.

Questions:
1) What is one of the key advantages of React?
It uses a virtual DOM to improve performance and efficiency.
2) What is the purpose of state in React?
State tracks and updates data that affects how a component renders and behaves.

## What Are Components in React
Components are the building blocks of React applications that allow developers to break down complex user interfaces into smaller, manageable pieces, making it easier to develop and maintain large-scale applications.

The two types of components in React are functional and class-based components. In modern React, developers use functional components

This UI is described using JSX, a syntax extension for JavaScript that looks similar to HTML but allows you to write UI elements in a more declarative way.

example:
```
function Greeting() {
  const name = "John";
  return (
    <h1 className="title">
      {/* The result will be Hello John */}
      Hello {name}
    </h1>
  );
}
```

### Component Naming
Use capital letter at the beginning of the component name. 
This is because React treats components with a capital letter as custom components, while elements with lowercase letters are considered built-in HTML elements.
When React encounters a lowercase tag, like <div> or <span>, it assumes it's a standard HTML element. However, if the component name starts with a capital letter, React will treat it as a user-defined component and render it accordingly. 

### Using a Component
To use this Greeting component in our application, we would write something like this:
```<Greeting />```

### Rendering Multiple Elements
example:
```
function Greeting() {
  const name = "John";
  // This will throw an error
  return (
    <h1>Hello {name}</h1>
    <p>Nice to meet you.</p>
  );
}
```
We are trying to add another sentence of Nice to meet you but it is not rendering on the page correctly.

There seems to be an error message instead. The error message says Adjacent JSX elements must be wrapped in an enclosing tag.

The reason why you are getting that error message is because multiple sibling elements need to be wrapped in a parent element. While you could wrap the h1 and p elements in a simple div, there is another way to satisfy that requirement.

### React Fragments
React fragments are used to group elements together. Here is what the revised example will look like:
```
import { Fragment } from "react";

function Greeting() {
  const name = "John";
  return (
    <Fragment>
      <h1>Hello {name}</h1>
      <p>Nice to meet you.</p>
    </Fragment>
  );
}
```
You can also choose to use empty JSX tags which can serve as shorthand for fragments:
```
function Greeting() {
  const name = "John";
  return (
    <>
      <h1>Hello {name}</h1>
      <p>Nice to meet you.</p>
    </>
  );
}
```
Questions:
1) What is the primary reason React uses className instead of class for HTML elements in JSX?
- class is a reserved keyword in JavaScript.
2) In the context of React components, what is JSX?
- A syntax extension for JavaScript that looks similar to HTML.
3) How would you render a Message component in React?
- <Message />

## How Do Default and Named Exports Work in React Components?
An export makes a component available to other files. An import allows a file to use a component that was exported elsewhere. In React projects, this is how components are reused and combined to build user interfaces.
### Using Default Exports
If we want to use our Cat component in another file, we need to first export it like this:
```
function Cat() {
  return (
    <div className="card">
      <h2>Mr. Whiskers</h2>
      <img
        src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/running-cats.jpg"
        alt="Cats walking on dirt ground near a bundle of straw."
      />
    </div>
  );
}
export default Cat;
```
You can also choose to export the component on the same line as the component definition like this:
```
export default function Cat() {
  return (
    <div className="card">
      <h2>Mr. Whiskers</h2>
      <img
        src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/running-cats.jpg"
        alt="Cats walking on dirt ground near a bundle of straw."
      />
    </div>
  );
}
```
### Importing a Default Export
```
import Cat from "./Cat";
```
### Using Named Exports
Unlike default exports, these must be imported using the exact name they were exported with (unless you rename them using the as keyword).
```
// Animals.jsx
export function Cat() {
  return <h2>Mr. Whiskers</h2>;
}

export function Dog() {
  return <h2>Fido</h2>;
}
```
We use the export keyword individually on each component. To use these in another file, we import them using curly braces:
```
import { Cat, Dog } from "./Animals";

export default function App() {
  return (
    <div>
      <Cat />
      <Dog />
    </div>
  );
}
```
When importing mixed exports, the default export comes first (without braces), followed by the named exports (inside braces):
```
// App.jsx
import Cat, { Dog } from "./Animals";

export default function App() {
  return (
    <div>
      <Cat />
      <Dog />
    </div>
  );
}
```
## What Is Vite?
One of the most popular tools for setting up projects is Vite. Vite, which means "fast" in French, is a build tool that aims to provide a faster development experience for modern web projects.
### Creating a New React Project
```
npm create vite@latest my-react-app -- --template react
```
This command creates a new React project named my-react-app using Vite's React template.

You can then open up the new project and see the React boilerplate code that Vite has provided for you.

The great thing about Vite is that it will only provide the files that are absolutely necessary to get started with your React project.
### Installing Dependencies
It installs the dependencies listed in the package.json file.
```
npm install
```
### The package.json File
The package.json file is a key configuration file in projects that contains metadata about your project, including its name, version, and dependencies. It also defines scripts, licensing information, and other settings that help manage the project and its dependencies.

### The node_modules Folder
Once the dependencies are installed, you should notice a new folder in your project called node_modules.

The node_modules folder is where all the packages and libraries required by your project are stored. This folder contains the actual code for the dependencies listed in your package.json file, including both your project's direct dependencies and any dependencies of those dependencies.

### Running the Project
To run your project, run the npm run dev command and open up a new browser tab at http://localhost:5173/.

## How Do You Pass Props from a Parent Component to a Child Component in React?
We can choose to nest this component inside another parent component or the root component like this:
```
function App() {
  return <Greeting />;
}

function Greeting() {
  const developerName = "Jessica";
  return <h1>Hi {developerName}!</h1>;
}
```
### Why Use Props?
While this code will run fine and display the result of Hi Jessica! on the screen, it is not that flexible of a component.

What if we wanted to display a different name like Naomi, Tom, or Oliver? This is where React props comes in. Props, which is short for properties, is the way for parent components to pass data down to the child component. Props can be of any type: strings, numbers, booleans, objects, or arrays.

### Passing Props to a Child Component
```
function App() {
  return <Greeting name="Jessica" />;
}

export default App;

function Greeting(props) {
  console.log(props);
  return <h1>Hi {props.name}!</h1>;
}
```
For the child component called Greeting we are now using props.name instead of hardcoding the name "Jessica". We are also logging props to the console which is showing as an object.

Then, inside of the parent App component, we are passing the value to the name prop so it can be passed down to the child. The result will be the same on the screen like earlier, but now we have created a more flexible component.
### Reusing the Child Component
```
function App() {
  return (
    <>
      <Greeting name="Naomi" />
      <Greeting name="Tom" />
      <Greeting name="Jessica" />
      <Greeting name="Oliver" />
    </>
  );
}
```
### Destructuring Props
```
function Greeting({ name }) {
  return <h1>Hi {name}!</h1>;
}
```
### The children Prop
React also provides a special prop called children. Any JSX you place between a component's opening and closing tags is passed to the component as children.
```
function Card({ children }) {
  return <div className="card">{children}</div>;
}

function App() {
  return (
    <Card>
      <h2>Hello</h2>
    </Card>
  );
}
```
In this case, the JSX inside <Card>...</Card> becomes the children prop. The rendered output in the DOM will be:
```
<div class="card">
  <h2>Hello</h2>
</div>
```
### Passing Multiple Props With the Spread Operator
```
function DeveloperCard({ name, age, country }) {
  return (
    <div className="developer-card">
      <h1>Developer: {name}</h1>
      <p>Age: {age}</p>
      <p>Country: {country}</p>
    </div>
  );
}

function App() {
  const developerObj = {
    name: "Alice",
    age: 30,
    country: "USA",
  };

  return (
    <div className="App">
      <DeveloperCard {...developerObj} />
    </div>
  );
}
```
This is particularly useful when working with arrays of objects and passing multiple sets of properties to child components. For example, you might have a list of developers where each object in the array has the same structure but represents a different person.
#### Using props in React makes your components more flexible and reusable, allowing you to build more complex UIs. However, it's important to note that props are immutable, meaning they cannot be changed once passed to a component. If you need to handle user input and modify data, you should use state instead. 
Questions:
1) In React, how do you pass a prop named message with the string Hello to a child component?
```<ChildComponent message="Hello" />```
2) How would you access a prop named userName inside a functional child component, assuming the props are passed as a props object?
```props.userName```
3) What is the correct way to pass all properties of an object as individual props to a child component?
```<ChildComponent {...objectName} />```

## How Does Conditional Rendering Work in React Components?
Conditional rendering in React allows you to create dynamic user interfaces. It is used to show different content based on certain conditions or states within your application.

The most common approaches of using conditional rendering includes using if statements, the ternary (?:) operator, and logical AND (&&) operator.

The simplest form of conditional rendering uses an if statement. Here's an example:
```
function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign in</h1>;
}
```
For simpler conditions, the ternary operator (?:) is often used directly within JSX. It allows for inline conditional rendering, which can make your code more concise:
```
function Greeting({ isLoggedIn }) {
  return <h1>{isLoggedIn ? "Welcome back!" : "Please sign in."}</h1>;
}
```
Another common pattern for conditional rendering is using the logical AND (&&) operator. This is particularly useful when you want to render something, or nothing, based on a condition:
```
function Notification({ message }) {
  return (
    <div>
      {message && <p>{message}</p>}
    </div>
  );
}
```

