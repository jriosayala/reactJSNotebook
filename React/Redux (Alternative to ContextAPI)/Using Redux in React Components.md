When using Redux in React, the `react-redux` package is needed in addition to the main `redux` package. As mentioned earlier in [[How Redux Works]], the basic flow of a state manager is to have only one store and a `reducer` function that handles the `dispatch` actions sent by the components (which must be subscribed to this context/store). The first step is to wrap the `<App />` component with a `Provider` and pass the created store as a prop. 
See the following example.
![[reduxStoreCodeSnippet.png| 600]]
At this point, everything has been setup to start managing a state globally and the next step to make usage of it is to set a subscription from any component that needs and [[Dispatching Actions From Inside Components|dispatch actions from it]]
### Key points
- `useSelector();`
The `useSelector` hook is a part of the `react-redux` library and is used to extract data from the Redux store state in a React functional component. It allows you to access the state managed by Redux and use it within your components without needing to pass the state down through props. Keep in mind that the usage of this hook also "automatically" subscribes the component to the store without the need of explicitly declaring it, and handles it's changes as a expected (it includes clearing the values of the state if the component would be removed).

### Key Points about `useSelector`:

1. **Access Redux State**:
    
    - The `useSelector` hook allows you to access the state from the Redux store by providing a selector function. This function takes the entire state as an argument and returns the part of the state you want to use.
2. **Re-Renders**:
    
    - The component using `useSelector` will re-render whenever the selected state changes. This ensures that your component always has the latest state from the Redux store.
3. **Memoization**:
    
    - You can use memoization techniques to optimize the selector function if it performs expensive calculations. Libraries like Reselect can help with this.
