jQuery, a library that made it easier to manipulate the DOM.

two other libraries that allow us to create dynamic web content  
1. React is a JavaScript library for building user interfaces.

1. In the React model, _a webpage is composed of **components**_ that have a life cycle and change state, which affects how they're rendered.
2. React introduces this notion of the **VirtualDOM**, which allows us to add and remove elements.
3. React allows us to insert JavaScript elements/components into VirtualDOM
4. React is created and maintained by Facebook and is used by many well known companies.

#### three important features to React

**1. modularity**  
Modularity allows us to organize the code into **reusable components** that can be connected together. This allows us to separate functionality into compartmentalize everything that we want to do.

**2. React provides lifecycle maintenance**  
This involves modifying the component based on its **state**, adding event listeners and simplifying the way in which components are rendered.

**3. JSX**  
React introduces a technology known as JSX, which allows us to **embed HTML right into our JavaScript**.

##### Further Explaination

Components are the core of React.  
_Components make up the nodes inside the VirtualDOM and each component includes and maintains a state that changes with events._  
The components independently maintain their state and applications can be configured to respond to the different component events.

##### DOM & VirtualDOM

**DOM **is the structural representation of all the HTML elements.

In React, the **VirtualDOM** selectively renders and re-renders the different parts of the tree, or the different nodes, based on state changes.

_The VirtualDOM is more efficient_ because _**it does the least amount of DOM manipulation when it comes to updating components.**_

###### visual example of how the normal DOM works.

When any node in the DOM is updated, for instance some HTML element, the browser will update or re-render all the nodes in the DOM as a reflection of the change.

###### visual example of how the normal DOM works.

In the VirtualDOM, React figures out which part of the DOM needs to change,  
and only changes the nodes that are affected.

**two steps, diff and reconciliation.**  
1. In the **diff** step React will to **identify the node that has changed**,  
2. In **reconciliation** **figure out which other nodes are affected by the change.** Then it will re-render only the nodes that were affected by the change and not re-render any of the other nodes.

##### Three steps to using React.

1. First, within the webpage's HTML you'll need to allocate some position where the React component will be dropped or rendered, for instance a div.

2. The React component is then implemented in JavaScript.  
   1. It has an initial state  
   2. It has events that could change the component's state during its lifecycle.  
   3. It has a render function which will be used to draw that component or generate its HTML.

3. last the component is dropped into the allocated position that came from step one.

###### Example

1. In our HTML page, create a div to represent a location where the React component will be placed.

   HTML  
   head tag:  
   include the React JavaScript. \(As with jQuery, React is not part of the web browser by default, so we'll need to include React in the page.\)

   body tag:  
   we'll have some div, which is where we'll place the React component.\( Sunch as Here I've labeled it with the ID container.\)  
   script tag: specifying the type  
   of the JavaScript which is text/**jsx**.

##### [JSX](http://buildwithreact.com/tutorial/jsx)

JSX is **JavaScript XML Syntax Transform**, it's a way of putting HTML right into our JavaScript and then converting it to React code. JSX is a technology that converts HTML to JavaScript, so that we can then use it in the JavaScript function that renders a React component.

1. value in "" is string, value in {} is other JS expressions, like if use a variable, then sytax: {var}; or boolean value {true}
2. one of the props is className, like class in JS. we can access props in definition of the component by this.props.name

###### Example

![](/assets/Screen Shot 2018-02-23 at 1.20.53 PM.png)

1. we've specified JSX as the type of JavaScript.
2. This function **ReactDOM.render**, is going to render an instance of the component into document.body

Notice that we're mixing the JavaScript, which is this and this, with HTML which is this. JSX allows us to do that in the appropriate places.

###### A full hello world example using react.

1. As before, we need to make sure that we include the react JavaScript files or  
   libraries in the header of our HTML.

2. Then we'll set up a div that we'll label with the id container. This is where we're going to insert or drop our React component.

3. Within the JavaScript tags, we'll use this function, **React-DOM.render** that specifies the HTML that we should put at that location. Using jsx\(javascript syntax\) we can embed HTML right into our JavaScript.Here, we'll just say Hello, React!  
   **The first argument:** specifies what we want to display  
   **The second argument:** specifies where we're going to display it.  
   We'll select that element by its ID, that will be the div that we've labelled container.

In the next few lessons, we'll dive much deeper into using React.  
We'll see how we define components and how write the functions that modify those components based on user events.  
We'll see how components interact with each other.  
And then finally look at real world tools that are used for developing React applications.

