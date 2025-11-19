Redux Toolkit (RTK) is the official, recommended way to write Redux logic. It provides a set of tools and best practices that simplify the process of writing Redux applications. Here are several reasons why you should consider using Redux Toolkit:
### `createSlice` function
An utility provided by the Redux Toolkit package that simplifies the process of creating Redux slices. A slice is a collection of Redux reducer logic and [[Dispatching Actions From Inside Components|actions]] for a single feature of your application. The `createSlice` function helps to reduce boilerplate code and makes it easier to manage the state and actions for a specific feature.

Redux Toolkit internally uses some packages to _automatically_ detect and prevent [[Dispatching Actions From Inside Components#Important Notes|direct state changes]], like this `state++;` (which is not recommended). 
### `configureStore` function
Similar to `configureStore()` provided by the native Redux package, `configureStore` creates a store , but it makes merging multiple reducers into one reducer easier thereafter and instead of passing a reducer function a configuration object where we then set a reducer property. 
### Dispatching Actions against the `createSlice` function
Now, one of the facilities that the `createSlice` function provides is to easily handle the dispatched actions, see the following example: 
```js
// usage of a slicer for counter
const counterSlicer = createSlice({
  name: "counter",
  initialState,
  reducers: {
    increment(state) {
      state.counter++;
    },
    decrement(state) {
      state.counter--;
    },
    increase(state, action) {
      state.counter = state.counter + action.payload;
    },
    toggleCounter(state) {
      state.showCounter = !state.showCounter;
    },
  },
});
```
To add extra information, it should be sent via the payload in the action. See usage example:
```jsx
<button onClick={() => dispatch(counterActions.increase(5))}>
    Increment by 5
</button>
```
### Adding State Slices
Remember that in order to create a new slicer, `createSlicer` function is needed, define the _name_, _initialState_ and it's _reducers_. It is recommended to put it in it's [[#Splitting Code|own file]] for better maintenance and readability. 
```js
import { createSlice } from "@reduxjs/toolkit";

const initialAuthState = { isAuthenticated: false };
const authSlicer = createSlice({
  name: "auth",
  initialState: initialAuthState,
  reducers: {
    login(state) {
      state.isAuthenticated = true;
    },
    logout(state) {
      state.isAuthenticated = false;
    },
  },
});
```
### Working with Multiple Slices
If multiple slicers have been created, they all will be merged into a single one, when configuring store an object gets passed and some keys are also defined. It is important to set descriptive and useful names to latter be referenced when selecting states.
```js
// Refering to the authReducer as `auth` and the same approach with `counter`. 
const store = configureStore({
  reducer: { auth: authReducer, counter: counterReducer },
});
```
### Reading and Dispatching From a New Slice
Following the approach of having a slicer into separate files and concerns exported as separated. The ideal flow would be to select only the state that is needed to dispatch the action and then implement it in the right place. Following this workflow, only states and pieces of the store needed are imported to avoid code repetition and improve readability. 
```js
// As stated before, only actions are imported and no other extras.
import { authActions } from "../store/authSlicer";
const Auth = () => {
  const dispatch = useDispatch();
  // Function that dispatches the action
  const loginHandler = (event) => {
    event.preventDefault();
    dispatch(authActions.login());
  };

  return (
    <main className={classes.auth}>
      <section>
        <form onSubmit={loginHandler}>
          <div className={classes.control}>
            <label htmlFor="email">Email</label>
            <input type="email" id="email" />
          </div>
          <div className={classes.control}>
            <label htmlFor="password">Password</label>
            <input type="password" id="password" />
          </div>
          <button>Login</button>
        </form>
      </section>
    </main>
  );
};
```

### Splitting Code
A nice development experience can be easily understanding the structure of the project, as it progressively grows it can be hard to understand certain functionality or parts of the application, therefore, a proper definition of components at every level is needed. For the global store, it is suggested to create a single file with the configuration of the entity and no more, _slicers_, _actions_ and _reducers_ should be defined in it's own folders or files, according to the project's needs. 

store.js
```js
import { configureStore, createSlice } from "@reduxjs/toolkit";
import counterReducer from "./counterSlicer";
import authReducer from "./authSlicer";

const store = configureStore({
  reducer: { auth: authReducer, counter: counterReducer },
});

export default store;
```

authSlicer.js 
```js
import { createSlice } from "@reduxjs/toolkit";

const initialAuthState = { isAuthenticated: false };
const authSlicer = createSlice({
  name: "auth",
  initialState: initialAuthState,
  reducers: {
    login(state) {
      state.isAuthenticated = true;
    },
    logout(state) {
      state.isAuthenticated = false;
    },
  },
});

// Export the actions generated by createSlice
export const authActions = authSlicer.actions;

// Export the reducer generated by createSlice
export default authSlicer.reducer;

```
Example of how to consume it
```jsx
import { useDispatch, useSelector } from "react-redux";
import { authActions } from "../store/authSlicer";

const Header = () => {
  // Selecting only the piece of state needed, take in mind that in this case `auth` is the key defined when configuring the store.
  const isAuth = useSelector((state) => state.auth.isAuthenticated);
  const dispatch = useDispatch();
  return (
    <header className={classes.header}>
      <h1>Redux Auth</h1>
      {isAuth && (
        <nav>
          <ul>
            <li>
              <a href="/">My Products</a>
            </li>
            <li>
              <a href="/">My Sales</a>
            </li>
            <li>
              // Dispatching the action
              <button onClick={() => dispatch(authActions.logout())}>
                Logout
              </button>
            </li>
          </ul>
        </nav>
      )}
    </header>
  );
};
```