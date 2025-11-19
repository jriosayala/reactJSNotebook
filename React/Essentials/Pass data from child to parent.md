Passing data from a child component to a parent component in React involves using callback functions. The parent component defines a function and passes it down to the child component as a prop. The child component then calls this function, passing the data as an argument. This allows the parent component to receive and handle the data from the child component.

Here’s a step-by-step guide on how to achieve this:

### Step 1: Define the Callback Function in the Parent Component

The parent component defines a function that will handle the data received from the child component. This function is then passed to the child component as a prop.

### Step 2: Pass the Callback Function to the Child Component

The parent component passes the callback function to the child component through props.

### Step 3: Call the Callback Function in the Child Component

The child component calls the callback function, passing the data as an argument.
### Example

Here’s a complete example demonstrating how to pass data from a child component to a parent component:

#### Parent Component

JavaScript

```jsx
import React, { useState } from 'react';
import ChildComponent from './ChildComponent';
function ParentComponent() {
	const [dataFromChild, setDataFromChild] = useState('');
	// Callback function to handle data from child   
	const handleDataFromChild = (data) => {
		setDataFromChild(data);
	};    
	return (
		<div>       
			<h1>Parent Component</h1>       
			<p>Data from Child: {dataFromChild}</p>       
			<ChildComponent onData={handleDataFromChild} />     
		</div>   
	); 
}  
export default ParentComponent;
```

#### Child Component

JavaScript

```jsx
import React, { useState } from 'react';
function ChildComponent({ onData }) {
	const [inputValue, setInputValue] = useState('');
	// Function to handle input change   
	const handleChange = (e) => {
	     setInputValue(e.target.value);
	};    
	// Function to send data to parent   
	const sendDataToParent = () => {
	     onData(inputValue);   
	};    
	return (
	     <div>       
	     <h2>Child Component</h2>       
	     <input 
		     type="text"
		     value={inputValue}
		     onChange={handleChange}
		     placeholder="Enter some data"
	     />       
	     <button onClick={sendDataToParent}>Send Data to Parent</button>
	     </div>   
	); 
}  
export default ChildComponent;
```

### Explanation

1. **Parent Component**:
    
    - The `ParentComponent` defines a state variable `dataFromChild` to store the data received from the child component.
    - The `handleDataFromChild` function is defined to update the state with the data received from the child component.
    - The `handleDataFromChild` function is passed to the `ChildComponent` as a prop named `onData`.
2. **Child Component**:
    
    - The `ChildComponent` defines a state variable `inputValue` to store the input value.
    - The `handleChange` function updates the `inputValue` state whenever the input changes.
    - The `sendDataToParent` function calls the `onData` prop (which is the `handleDataFromChild` function from the parent) and passes the `inputValue` as an argument.
3. **Interaction**:
    
    - When the user types in the input field in the `ChildComponent`, the `inputValue` state is updated.
    - When the "Send Data to Parent" button is clicked, the `sendDataToParent` function is called, which in turn calls the `handleDataFromChild` function in the `ParentComponent` with the current `inputValue`.
    - The `ParentComponent` updates its `dataFromChild` state with the data received from the child component, and the new data is displayed in the parent component.

### Summary

Passing data from a child component to a parent component in React involves using callback functions. The parent component defines a function to handle the data, passes it to the child component as a prop, and the child component calls this function with the data as an argument. This approach allows for effective communication and data flow from child to parent components.