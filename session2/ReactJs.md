## **Virtual DOM**
 - Virtual DOM is in-memory representation of Real DOM. It is
   lightweight JavaScript object which is copy (abstraction) of Real DOM.

> The DOM is fast. Adding and removing DOM nodes doesn’t take much more
> than setting a property on a JavaScript object.  What is slow,
> however, is the layout that browsers have to do whenever the DOM
> changes. Every time the DOM changes, browser need to recalculate the
> CSS, do layout, and repaint the web page. This is what takes time.

**How Does Virtual DOM Work?**

 - Each time the underlying data changes in a React , a new Virtual DOM
 representation of the user interface is created.
 - Updating the browser’s DOM is a three-step process in React : 
	 - Whenever anything may have changed, the entire UI will be re-rendered
   in a Virtual DOM representation.
	 - The difference between the previous Virtual DOM representation and
   the new one will be calculated.
	 - The real DOM will be updated with what has actually changed. 

**For reference:**

 - https://www.accelebrate.com/blog/the-real-benefits-of-the-virtual-dom-in-react-js/
 - https://hackernoon.com/virtual-dom-in-reactjs-43a3fdb1d130
## props

 - props are the properties that are passed to the components.
 
```
class Welcome extends React.Component {
  render() {
    return <h1>Hello {this.props.name}</h1>;
  }
}

const element = <Welcome name="Sara" />;

//Output: Hello Sara
```
In above example, name is a prop that is passed to Welcome component.

 - A component can also have default props.
 ```
 class Welcome extends React.Component {
  render() {
    return <h1>Hello {this.props.name}</h1>;
  }
}

Welcome.defaultProps = {
  name: "world",
};
//Output: Hello world
 ```
 ## State
 

 - Like props, state holds information about the component.
 ```
 class Button extends React.Component {
  constructor() {
    super();
    this.state = {
      count: 0,
    };
  }

  updateCount() {
    this.setState((prevState, props) => {
      return { count: prevState.count + 1 }
    });
  }

  render() {
    return (<button
              onClick={() => this.updateCount()}
            >
              Clicked {this.state.count} times
            </button>);
  }
}
```

**state vs props**

| Props      |  State |
|--|--|
|immutable  |mutable  |
|are used to pass data down from your view-controller|should be managed in your view-controller|
|props contains information set by the parent component (although defaults can be set) and should not be changed.|state contains “private” information for the component to initialise, change, and use on it’s own.|

## JSX
 - JSX is an XML-like syntax extension to ECMAScript without any defined semantics.
 - You can embed any JavaScript expression in JSX by wrapping it in curly braces.

```
const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);
```

 - After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects.This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions:
```
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```
## Component Hierarchy
 - When it comes to creating an application, we’ll have a single component at the top ,which will render everything else, calling in various different components to render different parts of the UI as required. 
 - This Parent component will hold  the  states and Child components receive that data in the form of props. 

**For more details:** 
https://www.ctheu.com/2015/02/12/how-to-communicate-between-react-components/

