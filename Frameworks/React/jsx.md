# JSX

## Basic:
- use `()` to write multiline code
- in ReactDOM.render 1st argument is element to render and 2nd is where to put it
- `className` instead of `class` on element
```js
import React from 'react';
import ReactDOM from 'react-dom';

const whatWantToRender = (
    <div>
        <h1>Something to render</h1>
    </div>
);
ReactDOM.render(whatWantToRender, document.getElementById('whereToPut'));
```

>In HTML tags which are single like `<br>`, `<img>` in JSX has to be with closed slash - `<br />, <img />`

## To create events on elements we should use camelCase of event name
```js
function myFunc(){
    console.log('myFunc');
}
// should use 'onClick, onMouseOver' etc
const someElements = (
    <div>
        <button onClick={myFunc}>Click me</button>
    </div>
);
```

## If Statements That Don't Work
This code will break:
```js
(
  <h1>
    {
      if (purchase.complete) {
        'Thank you for placing an order!'
      }
    }
  </h1>
)
```

One possible way.
Works, because the words `if` and `else` are not injected in between `JSX` tags. The `if` statement is on the outside, and no JavaScript injection is necessary.
```js
let message;

if (user.age >= drinkingAge) {
  message = (
    <h1>
      Hey, check out this alcoholic beverage!
    </h1>
  );
} else {
  message = (
    <h1>
      Hey, check out these earrings I got at Claires!
    </h1>
  );
}

ReactDOM.render(
  message, 
  document.getElementById('app')
);
```
2nd possible way is to use **ternary operator**
```js
function coinToss () {
  // Randomly return either 'heads' or 'tails'.
  return Math.random() < 0.5 ? 'heads' : 'tails';
}

const pics = {
  kitty: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-kitty.jpg',
  doggy: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-puppy.jpeg'
};

const img = <img src={pics[coinToss() === 'heads' ? 'kitty' : 'doggy']} />;

ReactDOM.render(
	img, 
	document.getElementById('app')
);
```

## Usage of the `&&`
```js
// judgmental will be true half the time.
const judgmental = Math.random() < 0.5;

const favoriteFoods = (
  <div>
    <h1>My Favorite Foods</h1>
    <ul>
      <li>Sushi Burrito</li>
      <li>Rhubarb Pie</li>
      {!judgmental && <li>Nacho Cheez Straight Out The Jar</li>}
      <li>Broiled Grapefruit</li>
    </ul>
  </div>
);
```

## Use `.map()`. If you want to create a list of JSX elements, then `.map()` is often your best bet
```js
const strings = ['Home', 'Shop', 'About Me'];

const listItems = strings.map(string => <li>{string}</li>);

<ul>{listItems}</ul>
```

## Key
```js
<ul>
  <li key="li-01">Example1</li>
  <li key="li-02">Example2</li>
  <li key="li-03">Example3</li>
</ul>
```
A key is a JSX attribute. The attribute's name is key. The attribute's value should be something unique, similar to an id attribute.

keys don't do anything that you can see! React uses them internally to keep track of lists. If you don't use keys when you're supposed to, React might accidentally scramble your list-items into the wrong order.

### Not all lists need to have keys. A list needs keys if either of the following are true:
- The list-items have memory from one render to the next. For instance, when a to-do list renders, each item must "remember" whether it was checked off. The items shouldn't get amnesia when they render.
- A list's order might be shuffled. For instance, a list of search results might be shuffled from one render to the next.

If neither of these conditions are true, then you don't have to worry about keys. If you aren't sure then it never hurts to use them!

### Get unique **Key**
```js
const people = ['Rowe', 'Prevost', 'Gare'];

const peopleList = people.map((person, i) => { // add 2nd argument 'i' unique index
        <li key={'persone_' + i}>{person}</li> // add it into the 'key'
    }
);
```

## React.createElement
You can write React code without using JSX at all!

The majority of React programmers do use JSX, and we will use it for the remainder of this tutorial, but you should understand that it is possible to write React code without it.

The following JSX expression:
```js
const h1 = <h1>Hello world</h1>;
```
can be rewritten without JSX, like this:
```js
const h1 = React.createElement(
  "h1",
  null,
  "Hello, world"
);
```
When a JSX element is compiled, the compiler transforms the JSX element into the method that you see above: React.createElement(). Every JSX element is secretly a call to React.createElement().