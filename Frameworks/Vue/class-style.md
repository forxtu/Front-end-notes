# Dynamic Class & Style binding
```js
// vue
data: {
    isActive: true,
    activeColor: 'red'
}
// bind class or style
<div v-bind:class="{active: isActive}"
     @click="isActive = !isActive"></div>
// bind multiple classes
<div :class="[red, {blue: isActive}]">
// Short form of `v-bind` is `:`
<div :style="{color: activeColor}"></div> 
```

```js
<div :style="{myStyle}"></div>
<input type="text" v-model="color">
<input type="text" v-model="width">

data:{
    // styles
    color: 'gray',
    width: 100,
    // classes
    attachRed: false
},
computed: {
    myStyle: function() {
        return {
            backgroundColor: this.color,
            width: this.width
        }
    },
    divClasses: function() {
        return {
            red: this.attachRed,
            blue: !this.attackRed
        }
    }
}
```