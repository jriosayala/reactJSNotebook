To define routes inside of a React Application, the `react-router-dom` package is needed for route definition. 
## Creating Browser Routes
Creating a route is as simple as using the `createBrowserRouter` function and passing routes as objects into an array. Every route needs to properties, it's path and it's element (commonly, the component to be used as a page).
### Router Provider
This component is in charge of providing the routes to the application, it needs one parameter to work and it's the Router Object (which is the one returned by the `createBrowserRouter`)
### Example of Creating a Browser Router

```jsx
const router = createBrowserRouter([{ path: "/", element: <Home /> }]);

function App() {
	return <RouterProvider router={router} />;
}```

## Navigating
Users navigate your application with `<Link>`, `<NavLink>`, and `useNavigate`

### Link 
 Using `<Link to="/route" />` prevents the browser from sending another HTTP request (which is the default action for requesting new data). Use `<Link>` when the link doesn't need active styling

### NavLink
Wraps `<Link />` with additional props for styling active and pending states.
- `NavLinkProps.end: boolen | undefined`
		Changes the matching logic for the active and pending states to only match to the "end" of the `NavLinkProps.to`. If the URL is longer, it will no longer be considered active.

### useNavigate
This hook allows the programmer to navigate the user to a new page without the user interacting.
### Children routes
A common pattern to use is nested routes, which helps with design and readability. Children or nested routes will be loaded regardless of the parent element; they will be appended. See the following example where `RootLayout` is shared alongside all other components. Of course, children can also contain other children and wrap elements as their parent.
```jsx
const router = createBrowserRouter([
  {
    path: "/",
    element: <RootLayout />,
    children: [
      { index: true, element: <HomePage /> },
      {
        path: "events",
        element: <EventsRootLayout />,
        children: [
          { index: true, element: <EventsPage /> },
          { path: ":eventId", element: <EventDetailPage /> },
          { path: "new", element: <NewEventPage /> },
          { path: ":eventId/edit", element: <EditEventPage /> },
        ],
      },
    ],
  },
]);
```
Keep in mind that the latest children in the tree will share every layout from the root component.
### `Outlet Component`
Renders the matching child route of a parent route or nothing if no child route matches.
### index property
A string indicating that an element should be render by default.