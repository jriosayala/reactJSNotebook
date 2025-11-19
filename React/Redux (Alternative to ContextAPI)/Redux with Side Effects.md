Working with asynchronous code and a global state can be hard to implement if logic is not placed properly, so, a good design patter, architecture or structure definition is needed.
For this example, a cart with items is going to be stored in some backend (firebase for this specific case), so a side effect should be performed. The following components are implemented and related to create the right actions. 
- `<Notification />`:
	- This is simple, an HTML element that shows a message according to the specified type passed as parameter, alongside title and message.
- `<Global Store />`
	- `cart-slice.js`: 
		- The slice responsible for managing actions related with the cart, such as adding and eliminating items. 
	- `ui-slice.js`:
		- The slice responsible for showing or hiding elements from the viewport (as notifications when cart is updated).
- `<App />` 
	- For this example, everything will be wrapped directly inside of the main app, even though is not the recommended practice for scaling large projects, later [[Action Creators|action creators]] will be implemented to show up the placement for those cases.

>[!NOTE]
> It is important to remember that a `reducer` must always be a side-free,  synchronous and pure function, meaning that it returns the same type.

For this example, a `useEffect()` hook will be used to set the cart info items[] and totalQuantity. To show up the capabilities and reusability of our notification component, an initial will be set and act as an informative one.
To do that, a dispatch action will be performed calling the UI Slicer with it's corresponding action, the fields needed are status, title and message, see the following declaration:
```jsx
// Don't forget to add the dependencies array to the useEffect; otherwise, it'll run infinitely in a loop on every initial render.

useEffect(() => {
	const sendCartData = async () => {
		dispatch(
			uiActions.setNotification({
				status: "pending",
				title: "Sending...",
				message: "Sending cart data",
		})
	);
},[])
```

Now that an initial notification is set and dynamically triggered.
For the following steps, an initial request will be sent to the back end part with the PUT method to update the information remotely with the local cart.
```jsx
useEffect(() => {
	const response = await fetch(
		"https://advanced-redux-d2c94-default-rtdb.firebaseio.com/cart.json",
		{ method: "PUT", body: JSON.stringify(cart) }
	);
// At this point, the cart state will be added as a dependency for the side effect
},[cart]);
```

In case there's an error, another notification will be sent as error type; otherwise, the expected behavior, success:
```jsx
// Dispatching a notification of type 'error'
if (!response.ok) {
  dispatch(
    uiActions.setNotification({
      status: "error",
      title: "Error!",
      message: "Sending cart data failed",
    })
  );
} else {
  dispatch(
    uiActions.setNotification({
      status: "success",
      title: "Success!",
      message: "Sent cart data successfully",
    })
  );
}
```

Finally the function gets executed with an extra catch method appended to any other unexpected error

```jsx
sendCartData().catch((error) => {
  dispatch(
	uiActions.setNotification({
	  status: "error",
	  title: "Error!",
	  message: "Sending cart data failed",
	})
  );
});
```

This code so far is good but has some minor issues that can impact the user experience such as overriding the global cart info (stored in the backend) at the initial render, so, in order to avoid that, an if statement should be declared 
```jsx
let isInitial = true;
function App() {
	useEffect(() => {
	// Necessary if statement to avoid clearing the cart at start
	if(isInitial) {
		isInitial = false;
		return;
	}
	}, []);
}
```