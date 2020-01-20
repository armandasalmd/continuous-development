## Introduction to React Router

When starting a new project, you need to determine which type of router to use. For browser based projects, there are `<BrowserRouter>` and `<HashRouter>` components.

The `<BrowserRouter>` should be used for dynamic - performs requests to server. `<HashRouter>` - for static websites

#### Rendering a \<Router\>

> Router components only expect to receive a **single child** element.

#### Routes

The `<Route>` component is the main building block of React Router. Anywhere that you want to only render content based on the location’s pathname, you should use a `<Route>` element.

```jsx
<Route path='/roster' component={Home} />
```

> When the current location’s pathname is matched by the path, the route will render a React element.

Query parameters do not effect the router:

```http
http://www.example.com/my-projects/one?extra=false
```

#### Switch

You can use the <Switch> component to group <Route>s. The <Switch> will iterate over its children elements (the routes) and only render the first one that matches the current pathname.

#### What \<Router\> renders?

Routes have three props that can be used to define what should be rendered when the route’s path matches. Only one should be provided to a `<Route>` element.

1. `component` — A React component. When a route with a component prop matches, the route will return a new element whose type is the provided React component (created using React.createElement).
1. `render` — A function that returns a React element 5. It will be called when the path matches. This is similar to component, but is useful for inline rendering and passing extra props to the element.
1. `children` — A function that returns a React element. Unlike the prior two props, this will always be rendered, regardless of whether the route’s path matches the current location.

Example:

```jsx
<Route path='/page' component={Page} />
const extraProps = { color: 'red' }
<Route path='/page' render={(props) => (
  <Page {...props} data={extraProps}/>
)}/>
<Route path='/page' children={(props) => (
  props.match
    ? <Page {...props}/>
    : <EmptyPage {...props}/>
)}/>

```

#### Path Params

The `:number` part of the path `/roster/:number` means that the part of the pathname that comes after `/roster/` will be captured and stored as `match.params.number`. For example, the pathname `/roster/`6 will generate a params object:
`{ number: '6' } // note that the captured value is a string`

#### Links

Anchor elements would refresh all page. Use `<Link>` instead

```jsx
import { Link } from 'react-router-dom'
function Header() {
	return (
		<header>
			<nav>
				<ul>
					<li>
						<Link to='/'>Home</Link>
					</li>
					<li>
						<Link to='/roster'>Roster</Link>
					</li>
					<li>
						<Link to='/schedule'>Schedule</Link>
					</li>
				</ul>
			</nav>
		</header>
	)
}
```
