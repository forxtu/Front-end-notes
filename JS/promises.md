# Promises
Simple example
```js
let promiseToCleanTheRoom = new Promise(function(resolve, reject){

    // cleaning the room

    let isClean = true;

    if(isClean) {
        resolve('Clean');
    } else {
        reject('not Clean);
    }

});

// when promise is resolved
promiseToCleanTheRoom.then(function(fromResolve){ // fromResolve = 'Clean' argument
    console.log('the room is' + fromResolve); // the room is Clean
}).catch(function(fromReject){
    console.log('the room is' + fromReject) // the room is not Clean - if rejected
})
```

More complex example
```js
let cleanRoom = function() {
    return new Promise(function(resolve, reject) {
        resolve('Cleaned The Room');
    });
};

let removeGarbage = function(message) {
    return new Promise(function(resolve, reject) {
        resolve(message + ' remove Garbage');
    });
};

let winIcecream = function(message) {
    return new Promise(function(resolve, reject) {
        resolve(message + ' won Icecream');
    });
};

// do them 'one by one'
// output: finished Clean The Room remove Garbage won Icecream
cleanRoom().then(function(result) {
    return removeGarbage(result);
}).then(function(result) {
    return winIcecream(result);
}).then(function(result) {
    console.log('finished' + ' ' + result);
})

// do them all 'in parallel' and after they are finished do something
// output: all finished
Promise.all([cleanRoom(), removeGarbage(), winIcecream()]).then(function() {
   console.log('all finished');
});

// if atleast one finished use 'race'
Promise.race([cleanRoom(), removeGarbage(), winIcecream()]).then(function() {
   console.log('one of them is finished');
});
```