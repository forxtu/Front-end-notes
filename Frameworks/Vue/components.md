# Components
```js
Vue.component('my-component', {
    // data is not an object but function in new components
    data: function(){
        return {
            msg: 'some msg'
        }
    },
    template: '{{msg}}'
})

// use new component in another components template
<div id="app">
    <my-component></my-component>
</div>
```
How to use with export import
```js
//main.js
import Vue from 'vue'
import App from './App'
import Component from './Component';
Vue.component('app-component', Component);
new Vue({
  el: '#app',
  render: h => h(App)
})
//in child component
export default {
    data() {
        return {

        }
    }
}
```



### main.js
```js
import Vue from 'vue'
import App from './App'

new Vue({
    el: '#app',
    template: '<App/>',
    components: { App }
})
```