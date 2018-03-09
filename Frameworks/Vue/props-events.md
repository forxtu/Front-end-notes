## Props
Pass data from Parent component to Child
```js
// in Child component
<p>{{ msg }}</p>
export default {
    props: {
        msg: {
            type: String,
            default: 'hi'
        }
    }
}
// in Parent component
<child-component :msg="newMsgFromParent"></child-component>
```

## Events - emit
Pass events from Child component to the Parent component
```js
//In Child component
<button @click='someEventChild'>Click</button>

methods: {
    someEventChild: function() {
        this.$emit('someEvent');
    }
}
//In Parent component define method
methods: {
    someEventParent: function() {
        alert('parent invoke from child');
    }
}
<child @someEventChild='someEventParent'>
```