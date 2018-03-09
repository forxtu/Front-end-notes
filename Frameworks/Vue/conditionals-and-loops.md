# Conditionals & loops
```js
// vue
data: {
    show: true,
    users: [
        {name: 'Bob'},
        {name: 'Alex'}
    ]
}
// if
<p v-if="show">This is shown</p> // add or remove element from dom
<p v-else>This is not</p>
// show
<p v-show="show">This is shown</p> // display block/none
// for loop
<li v-for="(user, index) in users" :key="item.id">
    {{user.name}}
</li> // Bob, Alex li elements
```