# What is Context in React?

## Props vs Context

Hello World!

While developing an application, we may need to pass data from one component to another. Sometimes the scenario would be a little complex where we need to pass data from n<sup>th</sup> children of component X to m<sup>th</sup> children of component Y.

Using "Props" is one of the ways to do it. However, it is a nested component, so we will have to chain multiple props until we reach our desired component.

Let us see an example:

![Props chaining](https://cdn.hashnode.com/res/hashnode/image/upload/v1671368599365/cSuxai9O5.png align="center")

In the above diagram, let's consider if we want to pass the value of the `val` variable from the component `X` to the component `c` , which is the 3rd child of the component `Y`. If we are passing via the props, then it would be like: we will be passing the val from `X` to `Y`, then `Y` to `a` , then `a` to `b` and then finally from `b` to `c` . This is such a long chaining of props from `X` to `c` . But, what if we have 100 children to component Y and we have to pass the value to the 100th component from Y. We cannot write 100 props in a chain. For this scenario, we can use the react `Context` API.

Context is a built-in API in react, introduced in v16.3. Context makes it possible for us to pass value from one component to another directly, without going through the component tree. Context stores the values separately, so the data is universally available throughout the application.

This is how the Context would work logically:

![Context in React](https://cdn.hashnode.com/res/hashnode/image/upload/v1671369981349/sviAhBLqU.png align="center")

## How to implement it?

It is very simple to create a context. We can create a context like this:

```javascript
import { createContext } from "react";
export const NameOfContext = createContext('initial value')
```

We will have to enclose the `App.js` with the `<NameofContext.provider>` tag and provide the context value and the function to change the context value as the value prop to it. We are doing it in App.js, so that the context value is available throughout the application, that is all the children of the App component. Below would be the implementation of it.

```javascript
import {NameOfContext} from './path/to/context'
export default function App() {
    return (
        // Here the "val" is the context value and "setVal" is the function used to change the context value
        <ThemeContext.Provider value={{val, setVal}}>
            <div className="main-container">
                .
                .
                .
                .
            </div>
        </ThemeContext.Provider>
```

If we want to set the context, we can do it by making use of `useContext` hook. Below would be its implementation.

```javascript
import {NameOfContext} from './path/to/context'

const Component = () => {
    // destructing the value and function with useContext hook
    const {val, setVal} = useContext(NameOfContext)
    return (
        <div>
            <!-- Assuming the val is 0 and on clicking the button, we are incrementing by 1 -->
            <button onClick={() => setVal(val+1)}>{val}</button>
        </div>
    )
}

export default Component
```

## Use case

I have used the Context in one of the use cases on my website. I was implementing a Dark theme for my website, where the theme should toggle between dark and light on clicking a button.

For implementing this, I've created a `ThemeContext` , which stores the theme value whether it is `'dark'` or `'light'` . I'll be setting the context value in the component which holds the toggle button. For the rest of the components, I'll get the context value and apply CSS classes based on the context value.

Below are a few implementations on my website:

I've created `ThemeContext.js` file, where I have created and initialized the context with `'light'` .

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671372274516/-2Mg2Oydz.png align="center")

In the `App.js` file, I've enclosed things inside `<ThemeContext.Provider>` tag.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671373307845/1eTvb_ba9.png align="center")

In the `header.jsx`, the file which holds the toggle button, I'm making use of the `theme` to set the styles for the themes and `setTheme` for updating the context when the button is clicked.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671373468306/pjUFx5XE0.png align="center")

In the `footer.jsx` file, I'm just consuming the `theme` value to set the CSS classes according to the theme.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671373602000/P3zJKT599.png align="center")

Just like the footer component, for the rest of the components, I've consumed the `theme` value and set the CSS classes accordingly.

You can take a look at how I've implemented it in the below repository:

%[https://github.com/sriram23/profile-fe] 

This is how it works on the actual website:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671373978381/xGWSi9965.gif align="center")

## Pros and Cons

### Pros

The following are a few advantages of Contexts:

*   Avoids long props chaining
    
*   Simple and easy to implement
    

### Cons

Context is an amazing feature, that makes our work easier. But it also has some cons and below is a few:

*   Debugging is difficult.
    
*   Might create unnecessary complexity if overused
    

That's all about the React Contexts. Hope this is useful. Looking forward to your comments and feedback. Thank you!