## Components

- In react, everything is structured as a component. A component is a piece of UI (User Interface) that has its own appearance and logic. It can be something like a button or a webpage. 

- React components are javascript functions which return markup.

```js
function MyButton() {
    return (
        <button>Click Me</button>
    );
}
```

- In react, all the components are by convention started with first letter to be capital.

## Export 

- Let's recall what you have learn in javascript. There are two types of export for a module:

1. `export` (Named Export)

    - You can export multiple values (functions, variables, classes) by name. 

    - When importing, you must use the exact name.

```js
// mathUtils.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

// app.js
import { add, subtract } from './mathUtils';
console.log(add(2, 3)); 
```

2. `export default` (Default Export)

    - You can export only one default thing per file. 
    
    - When importing, you can name it whatever you want (no curly braces).

```js
// greet.js
export default function greet(name) {
    return `Hello, ${name}!`;
}

// app.js
import greetUser from './greet';
console.log(greetUser('Dhairya')); 
```

- Hence, to keep the code clean, we use `export default` in react.

## JSX syntax

- In react, the above code's syntax are called `jsx` can they are used for convenience but, they are optional. Also, all the development tools supports the syntax.

- `jsx` is stricter than html. You have to close tags like `<br/>`. Also, in the return function of a component, you can not return multiple `jsx` tags. We must wrap them up in a `<>...</>` or `<div>...<div/>` tag. 

```js
function AboutPage() {
    return (
        <>
            <h1>About</h1>
            <p>Hello there.<br />How do you do?</p>
        </>
    );
}
```

## Styling 

- You can style the html elements using the `ClassName` attribute instead of `class`.

```js
<img className="avatar" />
```

- Then you write the CSS rules for it in a separate CSS file:

```js
.avatar {
    border-radius: 50%;
}
```

- You can add the CSS files either by using `link` tag in the main html file or if you are using any build tool then you must see its documentation.

## Displaying data

- You can use javascript in your react's components and also apply markup to it.

```js
return (
    <h1>
        {user.name}
    </h1>
);
```

- You can see that in the below example that in the style tag `{{}}` is used. It is not a special syntax but javascript written in the `style` object.

```js
const user = {
    name: 'Hedy Lamarr',
    imageUrl: 'https://i.imgur.com/yXOvdOSs.jpg',
    imageSize: 90,
};

export default function Profile() {
  return (
    <>
        <h1>{user.name}</h1>
        <img
        className="avatar"
        src={user.imageUrl}
        alt={'Photo of ' + user.name}
        style={{
            width: user.imageSize,
            height: user.imageSize
        }}/>
    </>
  );
}
```

## Conditional rendering 

- In react, there is no special syntax for conditionally rendering a component. You can use basic javascript for it.

```js
let content;

if (isLoggedIn) {
    content = <AdminPanel />;
} else {
    content = <LoginForm />;
}
return (
<div>
    {content}
</div>
);
```

## Working with list

- When you are given a list you can create a react component using javascript's functions like `map()` in array or `for` loop.

```js
const products = [
    { title: 'Cabbage', id: 1 },
    { title: 'Garlic', id: 2 },
    { title: 'Apple', id: 3 },
];

const listItems = products.map(product =>
    <li key={product.id}> {product.title} </li>
);

return (
<ul>{listItems}</ul>
);
```

## Responding to events

- For handling events, you can declare event handler in your component itself. 

```js
function MyButton() {
    function handleClick() {
        alert('You clicked me!');
    }

    return (
        <button onClick={handleClick}> Click me </button>
    );
}
```

- Notice here the `handleClick` function is passed as a reference to the onClick property similar to what you have seen in javascript event handling syntax.