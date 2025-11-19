Mutating data in the store in React can be done through the implementation and usage of the `useDispatch` hook provided by the Redux package. Take in mind that the action type must be the same as the [[Example of how to create a Redux Store|declared in the store]]. See the following example:

```jsx
import { useDispatch, useSelector } from "react-redux";

const Counter = () => {
  const dispatch = useDispatch();
  const counter = useSelector((state) => state.counter);

  return (
    <main>
      <h1>Redux Counter</h1>
      <div>{counter}</div>
      <div>
		// Using the same types of actions as the stores expects it
        <button onClick={() => dispatch({ type: "increment" })}>
          Increment
        </button>
        <button onClick={() => dispatch({ type: "decrement" })}>
          Decrement
        </button>
      </div>
    </main>
  );
};

export default Counter;
```

### Attaching Payloads to Actions
Send additional data to the action is as simple as adding an extra key: value to the store (reducer) and the action dispatcher. See the following example:
```jsx
if (action.type === "increase") {
	return {
	  counter: state.counter + action.amount,
	};
}
```

```jsx
// Usage example
<button onClick={() => dispatch({ type: "increase", amount: 5 })}>
	Increment by 5
</button>
```
### Working with Multiple State Properties
Same as before, in order to work with multiple state properties, an extra `key: value` is needed and therefore, used wherever is needed. See the following example:

```jsx
// Store definition
const initialState = { counter: 0, showCounter: false };
const reducer = (state = initialState, action) => {
	// Don't forget to also set the counter in other actions, otherwise,
	// afer the update the showCounter will be set to undefined and
	// therefore, a false value when evaluating
	if (action.type === "toggle") {
		return {
		  showCounter: !state.showCounter,
		  counter: state.counter,
		};
	}
}
```

`showCounter` property was added to manage the visibility of the counter. Here's the usage

```jsx
const Counter = () => {
	// Selecting only the part of the state needed with the help of useSelector hook
	const show = useSelector((state) => state.showCounter);
	
	return (
		<main className={classes.counter}>
		  <h1>Redux Counter</h1>
		  {show && <div className={classes.value}>{counter}</div>}
		  <div>
			<button onClick={() => dispatch({ type: "increment" })}>
			  Increment
			</button>
			<button onClick={() => dispatch({ type: "decrement" })}>
			  Decrement
			</button>
			<button onClick={() => dispatch({ type: "increase", amount: 5 })}>
			  Increment by 5
			</button>
		  </div>
		  <button onClick={() => dispatch({ type: "toggle" })}>
			Toggle Counter
		  </button>
		</main>
	);
};
```
### Important Notes:
- When working with states, you should never mutate the existing state because objects and arrays are reference values in JavaScript, instead always override it by returning a new state object
#redux #redux-toolkit #react