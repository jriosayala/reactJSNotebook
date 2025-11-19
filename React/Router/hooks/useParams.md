Returns the object of key/value pairs of the dynamic params from the current URL that were matched by the routes. Child routes inherit all params from their parent routes.
**Example**
```jsx
import { useParams } from "react-router"

function SomeComponent() {
  let params = useParams()
  params.postId
}

Assuming a route pattern like `/posts/:postId` is matched by `/posts/123` then `params.postId` will be `"123"`.

```