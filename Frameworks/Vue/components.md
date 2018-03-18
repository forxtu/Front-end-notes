# Components
```js
// register component globally
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

## Slots
Slots which doesn't have a slot name are `default` slots and will render into `<slot></slot>` tag
```js
// Parent
<child-component>
    <h1 slot="title">Slot tite</h1> // we can name slot to render it in different parts
    <p slot="text">slot text</p>
</child-component>

// Child
<div>
    <div class="title">
        <slot name="title"></slot> // render title here
    </div>
    <div class="text">
        <slot name="text"></slot> // render text here
    </div>
    <div class="slot-defaults">
        <slot name="subtitle">Default subtitle text</slot> // if we won't pass any data for this slot from parent it will show 'default' text
    </div>
</div>
```

## Dynamic components
Change content using dynamic components
```js
<template>
    <button @click="selectedComponent = 'First'">First</button>
    <button @click="selectedComponent = 'Second'">Second</button>
    <button @click="selectedComponent = 'Third'">Third</button>
    // Components dies after changing (destroyed life cycle), we can keep them alive using:
    <keep-alive>
        <component :is="selectedComponent">
            <h1>Default content</h1>
        </component>
    </keep-alive>
</template>

<script>
import First from './compoents/First.vue';
import Second from './compoents/Second.vue';
import Third from './compoents/Third.vue';
export default {
    data() {
        return {
            selectedComponent: 'appFirst'
        }
    },
    components: {
        appFirst: First,
        appSecond: Second,
        appThird: Third
    },
    // Dynamic components life cycles
    deactivated() {
        console.log('Deactivated!');
    },
    activated() {
        console.log('Activated!');
    }
}
</script>
```