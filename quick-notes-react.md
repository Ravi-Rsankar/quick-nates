# Quick-notes: React

Create a reactJS project and start  

```react
npx create-react-app my-app
cd my-app
npm start
```

## How React works and What is virtual DOM? 

React creates a virtual DOM. When state changes in a component it firstly runs a “**diffing**” algorithm, which identifies what has changed in the virtual DOM. The second step is **reconciliation**, where it updates the DOM with the results of diff.

The Virtual DOM is an abstraction of the HTML DOM. It is lightweight and detached from the browser-specific implementation details. It is not invented by React but it uses it and provides it for free. `ReactElements` lives in the virtual DOM. They make the basic nodes here. Once we defined the elements, `ReactElements` can be render into the "real" DOM.

Whenever a `ReactComponent` is changing the state, diff algorithm in React runs and identifies what has changed. And then it updates the DOM with the results of diff. The point is - it’s done faster than it would be in the regular DOM.

## What happens when you call "setState"? 

The first thing React will do when setState is called is merge the object you passed into setState into the current state of the component. This will kick off a process called reconciliation. The end goal of reconciliation is to, in the most efficient way possible, update the UI based on this new state. To do this, React will construct a new tree of React elements (which you can think of as an object representation of your UI). Once it has this tree, in order to figure out how the UI should change in response to the new state, React will diff this new tree against the previous element tree.

By doing this, React will then know the exact changes which occurred, and by knowing exactly what changes occurred, will able to minimize its footprint on the UI by only making updates where absolutely necessary.

this.setState() is only be called when a component is rendered and placed in the DOM. If the state needs to be set while loading the component with the values from the props, it can be done inside the constructor. 

```react
constructor(){
super()
this.state = this.props.something
}
```

## What is hot loading

**Hot loading** is the replacement of code in a running application without requiring a restart or reloading of the application. It is very useful when developing because you can see your changes as you make them thus giving immediate feedback

## JSX

- It describes what the UI should look like & it basically produces React Elements.
- After compilation JSX expressions become normal JS functions which are finally evaluated to plain JS objects. Therefore, we can use JSX expressions inside if statements, loops, pass them as an argument to functions as well as return them from some functions.
- So, now we know that JSX are more closer to plain JavaScript than HTML. Therefore, we use **camelCase** property naming convention instead of normal HTML attributes for tags. Eg: **className** instead of **class**, **htmlFor** instead of **for** and so on.
- Anything that we mention inside `{}` of a JSX expression will be evaluated as plain JavaScript.

## How is JSX converted to JavaScript objects

When an application is compiled, Babel breaks down the JSX code to Javascript element using the React.createElement() method. What `React.createElement()` does is basically takes in the element type, props associated with it and the childrens of that particular element as arguments and returns us a plain JavaScript object. 

The function definition of `React.createElement()` is:

```react
React.createElement(
  type,
  [props],
  [...children]
)
```

## Do we really need JSX to write React Applications ?

The answer is a big **NO**. React by itself doesn't require JSX. We could always use `React.createElement()` and not write JSX at all because it eventually is compiled to it.

But, imagine having too many nested tags, or building a complex UI. Would you prefer the simplicity of what JSX offers or the complexity of using `React.createElement()` ? And there are not such real world benefits of not using JSX. So, the answer is pretty obvious I think.

## Props and State 

The state is a data structure that starts with a default value when a Component mounts. It may be mutated across time, mostly as a result of user events.

Props (short for properties) are a Component’s configuration. Props are how components talk to each other. They are received from above component and immutable as far as the Component receiving them is concerned. A Component cannot change its props, but it is responsible for putting together the props of its child Components. Props do not have to just be data — callback functions may be passed in as props.

There is also the case that we can have default props so that props are set even if a parent component doesn’t pass props down.

Props and State do similar things but are used in different ways. The majority of our components will probably be stateless. Props are used to pass data from parent to child or by the component itself. They are immutable and thus will not be changed. State is used for mutable data, or data that will change. This is particularly useful for user input.

## Components

Components can refer to other components in their output. This lets us use the same component abstraction for any level of detail. A button, a form, a dialog, a screen: in React apps, all those are commonly expressed as components.

Typically, new React apps have a single `App` component at the very top. However, if you integrate React into an existing app, you might start bottom-up with a small component like `Button` and gradually work your way to the top of the view hierarchy.

## Functional components and Class components

A **functional**(a.k.a. **stateless**) component is just a plain javascript function which takes props as an argument and returns a react element. It accepts a single “props” object argument with data and returns a React element.

A stateless component has no state, it means that you can’t reach `this.state` inside it. It also has no lifecycle so you can’t use componentDidMount. Also `this.props` wont work in functional component and the `props` needs to passed as an argument to the function. 

```react
const MyStatelessComponent = props => <div>{props.name}</div>;
```

A **class** component has a state, lifecycle hooks and it is a javascript class which means that React creates instances of it. React should initialise the component class in order to call lifecycle hooks, call a constructor, initialise state and more.

```react
class MyComponentClass extends React.Component {
  render() {
    return <div>{this.props.name}</div>;
  }
}
```

### When should you use a stateless component:

A stateless component(or dumb) is just presentation of the state(props). It only can render props and it should only do that. A good example is a button component

You don’t need to have a state, lifecycle hooks or any internal variables inside a button component, you just simply need to render that.

### When should you use a class component:

if your component needs some data which cannot be passed as a prop use class component to get that data. If you need to keep UI state in your component(expandable blocks) so it’s a good place to keep that info in a components state.

## Key attribute

Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity:

```react
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li key={number.toString()}>    {number}
  </li>
);
```

The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use IDs from your data as keys:

```react
const todoItems = todos.map((todo) =>
  <li key={todo.id}>    {todo.text}
  </li>
);
```

When you don’t have stable IDs for rendered items, you may use the item index as a key as a last resort:

```react
const todoItems = todos.map((todo, index) =>
  // Only do this if items have no stable IDs  
  <li key={index}>    {todo.text}
  </li>
);
```

We don’t recommend using indexes for keys if the order of items may change.

## Controlled and Uncontrolled component

A controlled component doesn't have its own local state and it receives all the data via props and raises events whenever data needs to be changed. This component is entirely controlled by its parent. You could also call this a "dumb component". This is also referred as **single source of truth**

An uncontrolled component is one that stores its own state internally, and you query the DOM using a `ref` to find its current value when you need it. This is a bit more like traditional HTML.

```react
// Controlled:
<input type="text" value={value} onChange={handleChange} />

// Uncontrolled:
<input type="text" defaultValue="foo" ref={inputRef} />
// Use `inputRef.current.value` to read the current value of <input>
```

In most or all cases, you should use controlled components. 

## Lifecycle hooks

The component goes through few phases during their lifecycle. Each lifecycle has few methods which allow us to hook into certain moment during the lifecycle. The following are some frequently used lifecycle and their hooks.

### Mount

This is when an instance of a component is created and inserted into the DOM. React calls the below methods in order whenever the app is mounted

#### constructor

#### render

#### componentDidMount

### Update

Whenever the state is updated react calls the below methods in order.

#### render

#### componentDidUpdate

### Unmount

Component is removed from the DOM or is deleted. 

#### componentWillUnmount
