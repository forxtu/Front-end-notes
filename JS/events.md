# Events

```js
// onload
window.onload = function() {
    console.log('Window loaded!');
};
// onclick
var btn = document.querySelector('button');
btn.onclick = function() {
    console.log('Clicked!');
}
// if we create second event first will be overwritten
btn.onclick = function() {
    console.log('Also Clicked!'); // Also clicked!
}
```

## Event listeners
Multiple listeners
```js
var btn = document.querySelector('button');

// on click prints 2 listeners
btn.addEventListener('click', listener1);
btn.addEventListener('click', listener2);

setTimeout(function() {
    btn.removeEventListener('click', listener1); // removes listener1 after 2 seconds, should have the same event ('click' at this example)
}, 2000);

function listener1() {
    console.log('Listener 1');
}
function listener2() {
    console.log('Listener 2');
}
```

## Event behavior
Events by default is propagate
```js
var outer = document.querySelector('.outer');
var inner = document.querySelector('.inner');

outer.addEventListener('click', function(){
  alert('click outer');
}, true); // true - to change propagation order - even if we click 'inner' div check if outer was clicked first

inner.addEventListener('click', function(e){
    console.log(e.bubbles); // true
    e.stopPropagation(); // event won't bubble up and we will see only 'inner' alert
    alert('click inner');
});
```