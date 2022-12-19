# React Hooks

Hello World!

In this article let us see about the React functional components and the React hooks. Before diving into the Hooks, let us first see about the Stateful components and Stateless components.

### Stateful Components vs Stateless Components
Stateless components are also known as Functional Components in React. It is a plain Javascript function that takes props as parameters and returns a React Component.
Example:

```
import React from 'react';
export default function HelloWorld(props) {
    return <h1>Hello {props.name}!</h1>
}
```

Stateful components are also known as Class Components in React. It is a Javascript class extending React's Component class, that makes use of the render method which returns a React Component.
Example:

```
import React from 'react';
export default class HelloWorld extends React.Component {
    render() {
        return <h1>Hello {this.props.name}!</h1>
    }
}
```

### Components before hooks
Before the introduction of hooks, the class components were used in places where we need data other than that passed as props data. The state could be used only in class components. On the other hand, functional components are used in places where we require only props data. In simple words, the state cannot be used in functional components.

The lifecycle methods like `componentDidMount()` `componentDidUpdate()` `componentWillUnmount()` can be used only in class components and not in functional components.

### The introduction of Hooks
Hooks are introduced as a part of React version 16.8. Hooks enabled us to use class component features in the functional component itself. Hooks are nothing but the functions that helps us to implement state and lifecycle methods in functional components.

#### Things to keep in mind while using hooks

- React Hooks name start with 'use'. Example: `useState` `useEffect` `useReducer`
- React Hooks can be used only in Functional components and cannot be used inside class components
- Hooks can be used only on the top level of the components. Hooks cannot be used inside a conditional statement or a loop and cannot be nested inside a function.
- Hooks can be used in a React component and not in a plain Js file.

#### Popular Hooks

The following are some of the hooks that are frequently used:
 - useState
 - useEffect
 - useReducer
 - useRef

Let us briefly discuss each of the hooks.

#### useState
The useState is the hook used to implement state in a functional component.
Example: 

```
const [randomNumber, setRandomNumber] = useState(0)
``` 

Here, `randomNumber` will be the name of the variable, `setRandomNumber` is the function that is used to set the state's value. The argument that is passed to `useState` would be the initializer. In our case, it is zero. If we try to print or display the random number, the value printed/displayed would be `0`

We can change the state value just by calling the randomNumber method. Just like this

```
setRandomNumber(23)
``` 

Now, the value of `randomNumber` is been changed from `0` to `23`

#### useEffect
The `useEffect` is the hook that is used to implement life cycle methods in functional components.

The `useEffect` takes two params, the callback function and the variable to which the hook is subscribed. The second parameter is not mandatory.

If we are not providing the second argument, the hook will be get executed on every DOM change.

Let us see how we can implement lifecycle methods in `useEffect`

**ComponentDidMount:** 
Passing an empty array as the second parameter will make the `useEffect` hook act like componentDidMount

```
// Hooks
useEffect(()=>console.log("ComponentDidMount.."), [])

// Method
componentDidMount() {
    console.log("ComponentDidMount..");
}
``` 

**ComponentDidUpdate:**
We can achieve this by skipping the second parameter in `useEffect`. 

If we want to subscribe to any particular variable, then we can pass in that variable as the second parameter. In this case, the hook will get executed only when some change happens in the variable passed as the second argument

```
// Hooks
// Will be executed whenever there is a dom change
useEffect(()=>console.log("Random Number: ", randomNumber))
// Will be executed only when there is a change in randomNumber
useEffect(()=>console.log("Random Number: ", randomNumber), [randomNumber])

// Methods
componentDidUpdate() {
  console.log("Random Number: ", this.state.randomNumber)
}
``` 

**ComponentWillUnmount:**
We can achieve this by returning the function in the `useEffect` hook.

```
// Hooks
useEffect(() => {
    return ()=> {
        console.log("Component will unmount...");
    }
}, [])

// Methods
componentWillUnmount() {
   console.log("Component will unmount...");
}
```

We can use as many `useEffect`s in a single component.

#### useReducer
This is similar to that of reducer in redux. This hook enables us to have greater control over the states. This is how it can be implemented

```
const [count, dispatch] = useReducer(reducer, 0)
``` 

Here, `count` is the variable, `dispatch` is the method used to access the reducer, `reducer` is the reducer function that takes in the action, `0` is the initializer.

Let us see an example for the useReducer hook

```
import React, {useReducer} from 'react';

export default function Counter() {
  const reducer = (state, action) => {
    switch(action) {
      case 'increase':
        return ++state
      case 'decrease':
        return --state
    }
  }
  const [count, dispatch] = useReducer(reducer, 0)
  return(
    <div>
      <p>Counter: {count}</p>
      <button onClick={()=>dispatch('decrease')} disabled={count<1}>Decrease</button>
      <button onClick={()=>dispatch('increase')}>Increase</button>
    </div>
  )
}
``` 

In the above example, we increase and decrease the count by passing actions to the reducer.

I have played with the React Hooks in [this replit](https://replit.com/@sriramb/hooksExample#src/components/counter.jsx). Feel free to fork it and play around. Thank you and Happy Coding!







 
 
