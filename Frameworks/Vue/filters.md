# Filters
```js
//global filter
Vue.filter('uppercase', function(value){
    return value.toUpperCase();
});
//local filters
filters: {
    lowercase: function(value){
        return value.toLowerCase();
    }
}
//use filter
<p>{{ msg | uppercase | lowercase }}</p> // we can chain filters
```
Filter list with input
```js
// computed
<input v-model="filterText">
<ul>
    <li v-for="fruit in filteredFruits">{{fruit}}</li>
</ul>

computed: {
    filteredFruits() {
        return this.fruits.filter((element) => {
            return element.math(this.filterText);
        });
    }
}
```

## Mixins
To use global computed filters
```js
// in our component
import { fruitMixin } from './fruitMixin';

export default {
    mixins: [fruitMixin],
}

// fruitMixin.js file
export const fruitMixin = {
    data() {
        fruits: ['Apple', 'banana', 'mango'],
        filterText: ''
    },
    computed: {
    filteredFruits() {
        return this.fruits.filter((element) => {
            return element.math(this.filterText);
        });
    }
}
}
```
To create globally
```js
Vue.mixin({
    created() {
        console.log('Mixin created');
    }
})
```