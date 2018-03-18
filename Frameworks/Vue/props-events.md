## Props
Pass data from Parent component to Child
```js
// in Child component
<p>{{ msg }}</p>
export default {
    props: {
        msg: {
            type: String, // [String, Array] - multiple types
            default: 'hi'
        },
        obj: {
            type: Object, // if object or array for default use function  which returns an object
            default: function() {
                return {
                    myMsg: 'hey'
                }
            }
        },
        callbackProp: Function
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
<button @click='callbackProp()'>Click</button> // execute callback function passed from parent as prop

methods: {
    someEventChild: function() {
        this.$emit('someEventNameFromChild', this.someData);
    }
}
//In Parent component define method
methods: {
    someEventParent: function() {
        alert('parent invoke from child');
    },
    callBackParent: function() { // we can pass callback function as prop from parent to child #24
        console.log('callback parent');
    }
}
<child @someEventNameFromChild='someEventParent' :callbackProp="callBackParent"> // @someEventNameFromChild="someData = $event" - to pass data from row #34 "this.someData"
```