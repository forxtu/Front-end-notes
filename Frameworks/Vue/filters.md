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