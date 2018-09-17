# Iterators

```js
const randomNumber = (min, max) => {
  let number = Math.floor(Math.random() * max - min);
  return number;
};

// console.log(randomNumber(1, 20));

let randomItem = array => {
  return array[randomNumber(0, array.length)];
};

const makeDragon = () => {
  const dragonSizes = ["small", "medium", "big"];
  const dragonType = ["fire", "ice", "wind"];

  return `${randomItem(dragonSizes)} ${randomItem(dragonType)} dragon`;
};

console.log(makeDragon());
console.log(makeDragon());

let dragons = [];
let dragonArmy = dragons.concat(makeDragon(), makeDragon());

console.log(dragonArmy);

const iterator = dragonArmy[Symbol.iterator]();

console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());

// implementation
const dragonsArmyIterator = {
  [Symbol.iterator]: () => {
    return {
      next: () => {
        const maxDragons = Math.random() > 0.75;
        if (!maxDragons) {
          return {
            value: makeDragon(),
            done: false
          };
        }
        return {
          done: true
        };
      }
    };
  }
};

for (let dragon of dragonsArmyIterator) {
  dragon;
}
```
