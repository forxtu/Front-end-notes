## this
- `this` in `function` points where function was invoked and in `=>` where it was written
- if we call function with `()` `this` always will be equal to `window`

```js
var btn = document.querySelector('.btn');

function a(){
  console.log(this);
}

a(); // window

btn.addEventListener('click', function(){ // written in global but called in button object
  console.log(this); // html button object
});
// => this 
btn.addEventListener('click', () => { // written in global window object
  console.log(this); // window
});


// Inner functions (same with objects)
/* obj
    var obj = {
    log: function(){
        console.log(this); // obj
        var innerFunc =  function(){
            console.log(this); // window
        }
        var innerArrowFunc = () => {
            console.log(this); // obj
        }
        innerFunc(); // window
        innerArrowFunc(); // obj
    }
    obj.log();
*/
let outerFunc = function(){
    console.log(this);
    let that = this;
    let innerFunc = function() {
        console.log(this); // window
        console.log(that); // html button element (on click)
    }
    let arrowInnerFunc = () => {
        console.log(this);
    }
    innerFunc();
    arrowInnerFunc();
}

/* On click:
* - outerFunc: hmtl button element
* - innerFunc: window - because it's called with () `innerFunc()` even if it's inside of
*   the other function with object this
* - arrowInnerFunc: html button element - takes `this` from the outer function even if
*   called with () `arrowInnerFunc()`
*/
var btn = document.querySelector('.btn');
btn.addEventListener('click', outerFunc);

outerFunc(); // `window` always for all functions

// Object
var obj = {

}
```