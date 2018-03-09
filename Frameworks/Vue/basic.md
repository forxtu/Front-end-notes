# Vue js basics

## Set up with vue cli
- npm install -g vue-cli
- vue init webpack-simple 'nameOfProject'
- cd nameOfProject
- npm install
- npm run dev 

## Basic directives
Examples
```js
<span>{{msg}}</span> // interpolation
<span v-text="msg"></span>
<span v-html="msg"></span>
<span v-once>{{msg}}</span> // one time interpolation
```
