# Vue js basics

## Set up with vue cli
- npm install -g vue-cli
- vue init webpack-simple 'nameOfProject'
- cd nameOfProject
- npm install
- npm run dev 

## Instance Lifecycle
Whole life cycle
```js
new Vue({
    el: '#app',
    data: {
        title: 'The VueJS Instance'
    },
    beforeCreate: function() {
        console.log('beforeCreate()');
    },
    created: function() {
        console.log('created()');
    },
    beforeMount: function() {
        console.log('beforeMount()');
    },
    mounted: function() {
        console.log('mounted()');
    },
    beforeUpdate: function() {
        console.log('beforeUpdate()');
    },
    updated: function() {
        console.log('updated()');
    },
    beforeDestroy: function() {
        console.log('beforeDestroy()');
    },
    destroyed: function() {
        console.log('destroyed()');
    },
    methods: {
        destroy: function() {
            this.$destroy;
        }
    }
});

<div id='app'>
    <h1>{{ title }}</h1>
    <button @click="title = 'Changed'">Update title</button>
    <button @click="destroy">Destroy</button>
</div>

/* OUTPUT:
* beforeCreate()
* created()
* beforeMount()
* mounted()
* // *click Update title button*
* beforeUpdate()
* updated()
* // *click Destroy button*
* beforeDestroy()
* destroyed() // everything will stop work - removes JS logic
*/
```
