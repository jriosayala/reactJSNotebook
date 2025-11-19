In a React application, a global store refers to a centralized state management solution that allows you to manage and share state across multiple components. This approach helps to avoid "prop drilling" (passing props through many levels of components) and makes it easier to manage and update state consistently throughout the application.

### Why Use a Global Store?

1. **Centralized State Management**:
    
    - A global store provides a single source of truth for the application's state, making it easier to manage and reason about.
    - It simplifies the process of updating and retrieving state, as all state changes are handled in one place.
2. **Avoid Prop Drilling**:
    
    - Prop drilling occurs when you pass props through multiple levels of components to reach a deeply nested component.
    - A global store allows you to access state directly from any component, eliminating the need for prop drilling.
3. **Consistency**:
    
    - A global store ensures that all components have access to the same state, reducing the likelihood of inconsistencies and bugs.
    - It makes it easier to synchronize state changes across different parts of the application.

### Common Libraries for Global State Management

Several libraries can be used to implement a global store in a React application. Some of the most popular ones include:

1. **Redux**:
    
    - [[How Redux Works |Redux]] is a predictable state container for JavaScript apps.
    - It provides a centralized store, actions, and reducers to manage state changes.
    - Redux follows a strict unidirectional data flow, making it easier to understand and debug state changes.
2. **Context API**:
    
    - The Context API is a built-in feature of React that allows you to create a global store without the need for external libraries.
    - It is suitable for simpler use cases where you don't need the full power of Redux.
		[[React Vs React Context|See more about Redux vs React Context]]
1. **MobX**:
    
    - MobX is a state management library that uses observables to track state changes.
    - It provides a more flexible and less boilerplate-intensive approach compared to Redux.
4. **Recoil**:
    
    - Recoil is a state management library developed by Facebook.
    - It provides a more modern and flexible approach to state management, with features like atoms and selectors for fine-grained state management.
### Example Using Redux

Here’s a basic example of how to set up a global store using Redux in a React application:

#### Step 1: Install Redux and React-Redux

Bash

`npm install redux react-redux`

#### Step 2: Create Redux Actions

JavaScript

```js
// src/actions.js 
export const increment = () => ({   
	type: 'INCREMENT',
});
export const decrement = () => ({   
	type: 'DECREMENT,
});
```

#### Step 3: Create Redux Reducer

JavaScript

```js
// src/reducer.js 
const initialState = { count: 0 };
const counterReducer = (state = initialState, action) => {
	switch (action.type) {
		case 'INCREMENT':
			return { ...state, count: state.count + 1 };
		case 'DECREMENT':
			return { ...state, count: state.count - 1 };
		default:
			return state;   
	} 
};
export default counterReducer;
```

#### Step 4: Create Redux Store

JavaScript

```js
// src/store.js 
import { createStore } from 'redux';
import counterReducer from './reducer';
const store = createStore(counterReducer);
export default store;
```

#### Step 5: Provide the Store to the React App

JavaScript

```js
// src/index.js 
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import App from './App';
import store from './store';

ReactDOM.render(
	<Provider store={store}>     
		<App />   
	</Provider>,   
	document.getElementById('root') 
);
```

#### Step 6: Connect Components to the Store

JavaScript

```jsx
// src/App.js 
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement } from './actions';

function App() {
	const count = useSelector((state) => state.count);
	const dispatch = useDispatch();

	return (
		<div>       
			<h1>Count: {count}</h1>       
			<button onClick={() => dispatch(increment())}>Increment</button>
			<button onClick={() => dispatch(decrement())}>Decrement</button>
		</div>  
	);
}  
export default App;
```

### Example Using Context API

For simpler use cases, you can use the Context API to create a global store without external libraries:

#### Step 1: Create Context and Provider

JavaScript

```jsx
// src/Store.js 
import React, { createContext, useReducer, useContext } from 'react';
const initialState = { count: 0 };
const reducer = (state, action) => {
	switch (action.type) {
		case 'INCREMENT':
			return { ...state, count: state.count + 1 };
		case 'DECREMENT':       
			return { ...state, count: state.count - 1 };
		default:
			return state;   
	} 
};  

const StoreContext = createContext();

export const StoreProvider = ({children }) => {
	const [state, dispatch] = useReducer(reducer, initialState);

	return (
		<StoreContext.Provider value={{ state, dispatch }}>       
			{children}     
		</StoreContext.Provider>   
	); 
};  
export const useStore = () => useContext(StoreContext);
```
#### Step 2: Provide the Store to the React App

JavaScript

```jsx
// src/index.js 
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import { StoreProvider } from './Store';

ReactDOM.render(
	<StoreProvider>
		<App />
	</StoreProvider>,
	document.getElementById('root')
);
```

#### Step 3: Use the Store in Components

JavaScript

```jsx
// src/App.js 
import React from 'react';
import { useStore } from './Store';
function App() {
	const { state, dispatch } = useStore();
	
	return (
		<div>
			<h1>Count: {state.count}</h1>
			<button 
				onClick={() => dispatch({ type: 'INCREMENT' })}>Increment
			</button>
			<button 
				onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement
			</button>
		</div>   
	); 
}  
export default App;
```

### Summary

A global store in a React application provides a centralized way to manage and share state across multiple components. It helps avoid prop drilling, ensures consistency, and makes state management easier. Popular libraries for implementing a global store include Redux, Context API, MobX, and Recoil. Depending on the complexity of your application, you can choose the appropriate state management solution to fit your needs.