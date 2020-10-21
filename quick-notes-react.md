# Quick-notes: React

Create a reactJS project and start  

```
npx create-react-app my-app
cd my-app
npm start
```

#### What is virtual DOM? 

**The virtual DOM (VDOM)** is an in-memory representation of Real DOM. The representation of a UI is kept in memory and synced with the “real” DOM. It’s a step that happens between the render function being called and the displaying of elements on the screen. This entire process is called reconciliation.

VDOM renders only the updated component instead of re-rendering the entire DOM. This is done by **diffing**. 

#### What happens when you call "setState"? 

The first thing React will do when setState is called is merge the object you passed into setState into the current state of the component. This will kick off a process called reconciliation. The end goal of reconciliation is to, in the most efficient way possible, update the UI based on this new state. To do this, React will construct a new tree of React elements (which you can think of as an object representation of your UI). Once it has this tree, in order to figure out how the UI should change in response to the new state, React will diff this new tree against the previous element tree.

By doing this, React will then know the exact changes which occurred, and by knowing exactly what changes occurred, will able to minimize its footprint on the UI by only making updates where absolutely necessary.

#### What is the difference between state and props?

The *state* is a data structure that starts with a default value when a Component mounts. It may be mutated across time, mostly as a result of user events.

*Props* (short for properties) are a Component's configuration. They are received from above and immutable as far as the Component receiving them is concerned. A Component cannot change its props, but it is responsible for putting together the props of its child Components. Props do not have to just be data - callback functions may be passed in as props.

#### What is hot loading

**Hot loading** is the replacement of code in a running application without requiring a restart or reloading of the application. It is very useful when developing because you can see your changes as you make them thus giving immediate feedback

#### JSX

- It describes what the UI should look like & it basically produces React Elements.
- After compilation JSX expressions become normal JS functions which are finally evaluated to plain JS objects. Therefore, we can use JSX expressions inside if statements, loops, pass them as an argument to functions as well as return them from some functions.
- So, now we know that JSX are more closer to plain JavaScript than HTML. Therefore, we use **camelCase** property naming convention instead of normal HTML attributes for tags. Eg: **className** instead of **class**, **htmlFor** instead of **for** and so on.
- Anything that we mention inside `{}` of a JSX expression will be evaluated as plain JavaScript.

#### How is JSX converted to JavaScript objects

When an application is compiled, Babel breaks down the JSX code to Javascript element using the React.createElement() method. What `React.createElement()` does is basically takes in the element type, props associated with it and the childrens of that particular element as arguments and returns us a plain JavaScript object. 

The function definition of `React.createElement()` is:

```
React.createElement(
  type,
  [props],
  [...children]
)
```

#### Do we really need JSX to write React Applications ?

The answer is a big **NO**. React by itself doesn't require JSX. We could always use `React.createElement()` and not write JSX at all because it eventually is compiled to it.

But, imagine having too many nested tags, or building a complex UI. Would you prefer the simplicity of what JSX offers or the complexity of using `React.createElement()` ? And there are not such real world benefits of not using JSX. So, the answer is pretty obvious I think.