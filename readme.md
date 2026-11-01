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
class is a reserved keyword in JavaScript.
2) In the context of React components, what is JSX?
A syntax extension for JavaScript that looks similar to HTML.
3) How would you render a Message component in React?
<Message />