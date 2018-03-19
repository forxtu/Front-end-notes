# Window

## node vs element
Some nodes happens to be elements as well and some of them are not. And elements is always HTML elements.

## Location

```js
location
/*
    hash
    host
    hostname
    href
    origin
    pathname
    port
    protocol
    reload
    replace
    search
*/
```

## Create elements

```js
<div>
    <h1>Title</h1>
</div>

// js
var p = document.createElement('P');
p.textContent = 'A new paragraph!';

var div = document.querySelector('div');
var title = document.querySelector('h1');
title.appendChild(p); // add element inside an element (to the end)
div.insertBefore(p, title); // add p into div before title
```

## Delete elements

```js
<h1>Title</h1>
<ul>
    <li><a href="#">link 1</a></li>
    <li><a href="#">link 2</a></li>
    <li><a href="#">link 3</a></li>
</ul>

// js
var a = document.querySelectorAll('a')[1];
a.parentElement.removeChild(a); // removes 2nd 'a'

// not for old browsers
a.remove();
```