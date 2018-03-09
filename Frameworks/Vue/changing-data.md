## Computed
**Dependent Properties**
- All you use in `computed` can be used just as property which stored in a data object.
- Runs only if needed property changes.

For `methods` Vue doesn't know what stored inside it and will recalculate functions all the time even if no `secondCounter` inside it
**method `result` in methods will console.log `Method` even if we will click on `secondCounter`**
**computed `output` will console.log `Computed` only if we change properties which are stored in computed**
```js
<template>
    <div app="app">
        // methods
        // <button @click="increase">Increase</button>
        // <button @click="decrease">Increase</button>

        // computed 
        <button @click="counter++">Increase</button>
        <button @click="counter--">Increase</button>

        <button @click="secondCounter++">Increase second</button>

        <p>Counter: {{counter}}</p>
        <p>Result: {{result}}</p>

        <p>Result: {{result()}}</p> //method 'result'

        <p>Result: {{output}}</p> // computed
    </div>
</template>
new Vue({
    // Store data to be used
    data: {
        counter: 0,
        result: this.counter > 5 ? ... // data is not reactive so we can't just set logic here
        result: '',
        secondCounter: 0
    },
    // with methods we are duplicating code and it's hard to maintain
    // methods: {
    //     increase: function() {
    //         this.counter++;
    //         this.result = this.counter > 5 ? 'Greater 5' : 'Smaller 5';
    //     },
    //     decrease: function() {
    //         this.counter--;
    //         this.result = this.counter > 5 ? 'Greater 5' : 'Smaller 5';
    //     },
    //     It's possible to do something like this but we will have an issue anyway when try to click on 'secondCounter'
    //     result: function() {
    //         console.log('Method');
    //         this.counter > 5 ? 'Greater 5' : 'Smaller 5';
    //     }
    // }
    computed: {
        output: function() {
            console.log('Computed');
            return this.counter > 5 ? 'Greater 5' : 'Smaller 5';
        }
    }
})
```

## Watch
If you need asynchronous task to run
Execute code upot data changes

Set a property which you wanna watch
```js
<template>
    <div app="app">
        <button @click="counter++">Increase</button>
        <p>Counter: {{counter}}</p>
    </div>
</template>
new Vue({
    data: {
        counter: 0,
        secondCounter: 0
    },
    watch: {
        // watch some property (in that case 'counter') and if it changes do something (set counter to 0 after 2 seconds)
        counter: function(value) {
            setTimeout(() => {
                this.counter = 0;
            }, 2000)
        }
    }
})
```