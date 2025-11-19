Rendering an element outside of the component scope/tree in React can be achieved using a technique called "portals." Portals provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

### Use Case for Portals

Portals are useful for scenarios where you need to render elements outside the normal DOM hierarchy, such as:

- Modals
- Tooltips
- Popovers
- Dropdowns

### How to Create a Portal

1. **Create a DOM Node for the Portal**:
    
    - You need a DOM node outside the root element where the React app is mounted. This can be done by adding a div with an id in your HTML file.
2. **Use ReactDOM.createPortal**:
    
    - Use the `ReactDOM.createPortal` function to render the children into the specified DOM node.

### Example

Here’s a step-by-step example of how to create and use a portal in React:

#### Step 1: Create a DOM Node for the Portal

Add a div with an id (e.g., `portal-root`) in your HTML file, outside the root element where your React app is mounted.

HTML, XML

```html
<!DOCTYPE html> 
<html lang="en"> 
<head>
	<meta charset="UTF-8">   
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>React Portal Example</title> 
</head> 
<body>   
	<div id="root"></div>   
	<div id="portal-root"></div> <!-- Portal root element --> 
</body> 
</html>
```

#### Step 2: Create a Portal Component

Create a component that uses `ReactDOM.createPortal` to render its children into the `portal-root` element.

JavaScript

```js
import React from 'react';
import ReactDOM from 'react-dom';
function Portal({ children }) {
	const portalRoot = document.getElementById('portal-root');
	return ReactDOM.createPortal(children, portalRoot); 
}  
export default Portal;
```

#### Step 3: Use the Portal Component

Use the `Portal` component to render elements outside the component tree. For example, you can create a modal component that uses the `Portal` component to render its content.

JavaScript

```js
import React, { useState } from 'react';
import Portal from './Portal';
function App() {
	const [isModalOpen, setIsModalOpen] = useState(false);
	const openModal = () => {
	     setIsModalOpen(true);
	};    
	const closeModal = () => {
	     setIsModalOpen(false);   
	};    
	return (     
		<div>
			<h1>React Portal Example</h1>
			<button onClick={openModal}>Open Modal</button>
			{isModalOpen && (
				<Portal>
					<div className="modal">
						<div className="modal-content">
							<h2>Modal Title</h2>
							<p>This is a modal rendered using a portal.</p>
							<button onClick={closeModal}>Close Modal</button>
						</div>           
					</div>         
				</Portal>       
			)}     
		</div>   
	);
}  
export default App;
```

#### Step 4: Add Some Styling

Add some basic styling for the modal to make it look better.

CSS

```css
/* Add this CSS to your styles.css or equivalent file */ 
.modal {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background: rgba(0, 0, 0, 0.5);
	display: flex;
	justify-content: center;
	align-items: center;
}  
.modal-content {
	background: white;
	padding: 20px;
	border-radius: 5px;
	box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}
```

### Summary

Portals in React allow you to render elements outside the normal DOM hierarchy of the parent component. This is particularly useful for UI elements like modals, tooltips, and dropdowns that need to be rendered at a different place in the DOM tree. By using `ReactDOM.createPortal`, you can specify a DOM node where the children should be rendered, providing greater flexibility in how you structure your application.