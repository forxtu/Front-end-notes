# Mixins

```js
function humanFactory(obj) {
  let crying = false;
  
  return Object.assign({}, obj, {
    cry() {
      crying = true;
      return this;
    },  
    isCrying() {
      return crying;
    }   
  });
}

let human = new humanFactory({});

console.log(human.cry().isCrying());

// super factory
function superFactory(obj) {
  let fly = false;
  
  return Object.assign({}, obj, {
    flyEvent() {
      fly = true;
      return this;
    },
    isFlying() {
      return fly;
    }
  });
}

let superman = humanFactory(superFactory({}));

console.log(superman); // everything from humanFactory and superFactory
```