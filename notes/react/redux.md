## Redux crash course

Redux principles:

1. ONE application STATE OBJECT managedby ONE STORE
1. The only way to change the state is to emit an action, an object describing what happened
1. To specify how the state tree is transformed by actions, you write pure reducers

-   [Documentation](https://redux.js.org/)
-   [Youtube video source](https://www.youtube.com/watch?v=93p3LxR9xfM&feature=youtu.be)
-   [Wonderful blog post](https://www.freecodecamp.org/news/understanding-redux-the-worlds-easiest-guide-to-beginning-redux-c695f45546f6/)

In react you have components which share the same state.

> Redux is a predictable state container for JavaScript apps.
> It helps you write applications that behave consistently…

It provides you with a great developer experience, and makes sure that the testability of your app isn’t sacrificed for any of those.

#### Step 1

> The Redux Store can be likened to the Bank Vault. It holds the state of your application — and keeps it safe.

Have a single source of truth: The state of your whole application is stored in an object tree within a **single Redux store**.

! ONE application STATE OBJECT managedby ONE STORE !

**BANK VAULT = REDUX STORE**

#### Step 2

`action`s let redux know how to change `state in store`:

-   State is read-only
-   The only way to change the state is to emit an action, an object describing what happened.

If we chose to represent that process in a simple Redux application, your action to the bank may be represented by an object.

```js
{
  type: "WITHDRAW_MONEY",
  amount: "$10,000"
}
```

In the context of a `Redux` application, this object is called an **action**! It **always has a type field** that describes the action you want to perform. In this case, it is `WITHDRAW_MONEY`.

**Whenever you need to change/update the state of your Redux application, you need to dispatch an action.**

#### Step 3

> The `Cashier` is to the bank what the `reducer` is to Redux.

**CASHIER = REDUCER**
If you want to update the state of your application, you convey your action to the reducer — our own Cashier.
This process is mostly called dispatching an action.

<dl>
	<dt>Dispatch</dt>
	<dd>send off to a destination or for a purpose</dd>
</dl>

> To specify how the state tree is transformed by actions, you write pure reducers.

For now, what’s important is to understand that, to update the state of your application (like you do with `setState` in React,) your actions must always be sent off (dispatched) to the reducers to get your `new state`.

most important Redux actors are: the **store**, the **reducer** and an **action**.

In a nutshell, the Cashier and Vault are always in sync. Great buddies!
The same may be said for a Redux STORE (our own Vault,) and the Redux REDUCER (our own Cashier)
The REDUCER always “talks” to the STORE. Just like the Cashier stays in sync with the Vault.

> The Reducer is the only mandatory argument passed into createStore()
> Reducers are the most important concept in Redux.

Our Cashier is a pretty important person, huh?

**Redux Reducer is just a function**. A function that takes in two parameters. The first being the STATE of the app, and the other the ACTION

Standard reduce example:

```js
let arr = [1, 2, 3, 4, 5]
let sum = arr.reduce((x, y) => x + y)
console.log(sum) //15
```

Like `Array.reduce()`, `createStore()` is responsible for passing the arguments into the reducer.
The reducer is just a function

> A reducer always returns something. In the initial Array.reduce()reducer example, we returned the sum of the accumulator and current value.

> For a Redux reducer, you always return the new state of your application.

#### Summary

-   Redux is a predictable state container for JavaScript apps.
-   The createStore factory function from Redux is used to create a Redux STORE.
-   The Reducer is the only mandatory argument passed into createStore()
-   A REDUCER is just a function. A function that takes in two parameters. The first is the STATE of the app, and the other is an ACTION.
-   A Reducer always returns the new stateof your application.
-   The Initial State of your application, initialState is the second argument passed into the createStore function call.
-   Store.getState() will return the current state of your application. Where Store is a valid Redux STORE.

#### Step 4

Creating actions:

```js
{
	type: "withdraw_money",
	payload: {
		amount: "\$4000"
	}
}
```

That’s what an action is.

```js
function reducer(state, action) {
	//return new state
}
```

To handle the actions passed into the reducer, you typically write a switch statement within your reducer, like this:

```js
function reducer(state, action) {
	switch (action.type) {
		case 'withdraw_money':
			//do something
			break
		case 'deposit-money':
			//do something
			break
		default:
			return state
	}
}
```

With a Redux app, you can’t use setState() to update the state object managed by Redux. You have to dispatch an action first.

In a Redux app, every action flows through the reducer.

As I explained earlier, whenever there’s an intent to update the application state, an action must be dispatched.

---

It is common to create three different folders within your app directory, and name each after these actors. `the reducer, actions,and store.`

Create a store / vault
`store/index.js`

```js
import { createStore } from 'redux'
import reducer from '../reducers'

const initialState = { tech: 'React ' }
export const store = createStore(reducer, initialState)
```

> Now, if we need the store anywhere within our app, we can safely import the store, as in import store from "./store";

The only reason we dispatch an action is because we want a new application state!

After state is updated cia reducer. If you want the updates, you’ve got to subscribe to them.

> The argument passed into store.subscribe() is a **function**, and it will be invoked whenever there’s a state update.

#### Summary

-   Unlike setState() in pure React, the only way you update the state of a Redux application is by dispatching an action.
-   An action is accurately described with a plain JavaScript object, but it must have a type field.
-   In a Redux app, every action flows through the reducer. All of them.
-   By using a switch statement, you can handle different action types within your Reducer.
-   Action Creators are simply functions that return action objects.
-   It is a common practice to have the major actors of a redux app live within their own folder/directory.
-   You should not mutate the state received in your Reducer. Instead, you should always return a new copy of the state.
-   To subscribe to store updates, use the store.subscribe() method.
