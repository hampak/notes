# When to useReducer

When we want to create and maintain dynamic state values within our React application (or frameworks based on React), the first hook that comes to our mind is the `useState` hook. However, people forget that there's another hook that functions similarly to the useState hook.

The **useReducer** hook.

When should we use the useReducer hook? We can use this hook when **maintaining state values with complex data structures**.

![Ummm](ummm.jpg)

So for example, if your state value looks something like this:
```js
const user = {
  name: "Timothy",
  skills: ["javascript", "React", "NextJS", "Redux"],
  hobbies: [
    {name: "Piano", desc: "Played the piano for about 8 years"},
    {name: "Netflix", desc: "Favorite show is How I met your Mother"}
  ]
}
```

Then you should probably use the `useReducer` hook. Let's dive into it then.
<br><br>
## Da fundahmentals

Before we start coding with the useReducer hook, we must know three very important concepts to fully understand this hook.

**Dispatch, Action,** and **Reducer**.

<br>First, let's look at **Dispatch**.

In simple terms, when we say "dispatch", it means to demand a certain action to be executed. In frontend terms, we call this "dispatching an action object". It's simply **the action** of telling useReducer to do something.

<br>**Action**.

From the explanation above, I explained that **Dispatch** is simply the action of telling useReducer to execute a specific task. The **specific task** here would be the **Action**.

For example, let's say that we're in a e-commerce website. In this website's navbar, there is a shopping cart icon and the icon has a number indicating how many items are currently in the cart. Whenever we click on a button named "Add to cart", that number will change.

Clicking the button(EventHandler) would be the action of telling the app what to do. Hence, it would be **Dispatching** an action. Telling the app **what** to do (in this case, changing the number) would be the **Action**.

<br>**Reducer**

The **Reducer** will receive the action object and update the state.

Let's visualize this process with code:

```jsx
import React, {useState, useReducer} from "react";

const reducer = (state, action) => {
  switch(action.type) {
    case "addItem":
      return state + 1;
    default:
      return state;
  }
}

const shoppingApp = () => {
  const [items, dispatch] = useReducer(reducer, 0)
  
  return (
    <div>
      <img alt="cart icon"/>
      <p>Items: {items}</p>
      
      ...
      
      <button onClick={() => {
        dispatch({type: "addItem", payload: items})
      }}>Add to cart</button>
    </div>
  )
}
```

When we click on the `Add to cart` button, the state changes successfully.

Now, let's break down the code.

<br>First, we must get familiarized with this syntax

```jsx
const [state, dispatch] = useReducer(reducer, initialState)
```

In the code above, we can see that 
