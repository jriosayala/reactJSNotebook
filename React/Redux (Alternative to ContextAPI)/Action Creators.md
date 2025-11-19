Tunk:
	A function that ==delays an action== until later
>[!THUNK]
>An action creator function that does **NOT** return the action itself but instead another function which eventually returns the action.

When working with Redux Toolkit, it not only allow us to dispatch object of action types but also action creators. When a function is dispatched, Redux automatically handles the execution of the function. See the following example:

### Parent component calling for the sendCartData function

```jsx
useEffect(() => {
	// By adding this line, the first time it executes, prevents the dispatch from being called
	if (isInitial) {
		isInitial = false;
		return;
	}
	
	if (cart.changed) {
		// Dispatching an action creator
		dispatch(sendCartData(cart));
	}
	
	// Dispatch dependency will never trigger the useEffect, only cart
}, [cart, dispatch]);
```


`sendCartData` is the function in charge of handling the request, we can slice it into three main parts for a better understanding of what is happening.
```jsx
// Main function that receives the cart as param and returns a thunk function
const sendCartData = (cart) => {}
```

### Sending cart data notification

function returned by the main one (`sendCartData`), the `thunk`
```jsx
async (dispatch) => {
	dispatch(
		uiActions.setNotification({
			status: "pending",
			title: "Sending...",
			message: "Sending cart data",
		}),
	);
};
```

### The Request 
`sendRequest` function that handles the request for updating the backend, the `items` array and the `totalQuantity` are sent as a string in the body. If the fetching of data fails, it throws an error which is then caught by the following block of code.
```jsx
const sendRequest = async () => {
	const response = await fetch(
		"https://advanced-redux-d2c94-default-rtdb.firebaseio.com/cart.json",
			{
			  method: "PUT",
			  body: JSON.stringify({
				items: cart.items,
				totalQuantity: cart.totalQuantity,
			  }),
			},
	);
	if (!response.ok) {
		throw new Error("Sending cart data failed");
	}
};
```

### The actual result of the request
In this block the  `sendRequest` function is called, a notification will be dispatched either the request throws an error or is returns a success with it's proper information.

```jsx
try {
	await sendRequest();
	dispatch(
		uiActions.setNotification({
		  status: "success",
		  title: "Success!",
		  message: "Sent cart data successfully",
		}),
	);
} catch (error) {
	dispatch(
		uiActions.setNotification({
		  status: "error",
		  title: "Error!",
		  message: error.message,
		}),
	);
}
```

### Explained Flow
Here's a graphical description of what is occurring since the function is called from the parent component.
![[action creator flow explained|600x300]]
#redux #redux-toolkit #thunk #action-creator