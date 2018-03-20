# Directives

## Basic directives
Examples
```js
<span>{{msg}}</span> // interpolation
<span v-text="msg"></span>
<span v-html="msg"></span>
<span v-once>{{msg}}</span> // one time interpolation
```

## Directive hooks
We will use `bind` and `update` the most offen
```js
bind(el, binding, vnode) // One directive is Attached - readonly
inserted(el, binding, vnode) // inserted in parent node
update(el, binding, vnode, oldVnode) // once component is Updated (without Children)
componentUpdated(el, binding, vnode, oldVnode // once component is Updated (with Children)
unbind(el, binding, vnode) // once directive is removed
```

## Custom directives
### Register Globally
```js
Vue.directive('highlight', {
    bind(el, binding, vnode) {
        // el.style.backgroundColor = 'green'; // v-highlight on the element make background of element green
        // el.style.backgroundColor = binding.value;  // v-highlight="'red'" set value

        // v-highlight:background.delayed="'red'" set delay modifier. We can chain modifiers .delayed.anotherModifier
        var delay = 0;
        if(binding.modifiers['delayed']) {
            delay = 3000;
        }
        setTimeout(() => {
            /* v-highlight:background="'red'"
            *  with argument 'background' sets background color, without argument sets 'color' to red
            */
            if(binding.arg == 'background') {
                el.style.backgroundColor = binding.value;
            } else {
                el.style.color = binding.value;
            }
        }, delay)
    }
}); 

// in template usage
<p v-highlight>Color this</p> // add green background
<p v-highlight="'red'">Color this</p> // if we use binding.value use with value here
<p v-highlight:background="'red'">Color this</p> // :background argument
<p v-highlight:background.delayed="'red'">Color this</p> // .delayed modifier
```

### Register locally
```js
export default {
    directives: {
        'local-highlight': {
            bind(el, binding, vnode) {
                // extend global directive
                var delay = 0;
                if(binding.modifiers['delayed']) {
                    delay = 3000;
                }
                // blink modifier
                if(binding.modifiers['blink']) {
                    let mainColor = binding.value.mainColor; // if we pass object in template
                    let secondCOlor = binding.value.secondCOlor; // if we pass object in template
                    let curentColor = mainColor;
                    setTimeout(() => {
                        setInterval(() => {
                            if(curentColor === secondCOlor ? curentColor = mainColor : curentColor = secondCOlor);
                        }, binding.value.delay); // if we pass object in template
                        if(binding.arg == 'background') {
                            el.style.backgroundColor = curentColor;
                        } else {
                            el.style.color = curentColor;
                        }
                    }, delay)
                } else {
                    setTimeout(() => {
                        if(binding.arg == 'background') {
                            el.style.backgroundColor = binding.value.mainColor;
                        } else {
                            el.style.color = binding.value.mainColor;
                        }
                    }, delay)
                }
            }
        }
    }
}

// in template usage
<p v-local-highlight:background.delayed.blink="{mainColor: 'red', secondColor: 'green', delay: '500'}">Color this</p>
```