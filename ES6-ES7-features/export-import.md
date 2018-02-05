# Exports & Imports

You got two different types of exports: default (unnamed) and named exports:
```javascript
default => export default ...; 
named => export const someData = ...; 
```
You can import **default exports** like this:
```javascript
import someNameOfYourChoice from './path/to/file.js'; 
```
**Named exports** have to be imported by their name:
```javascript
import { someData } from './path/to/file.js'; 
```
A file can only contain one default and an unlimited amount of named exports. You can also mix the one default with any amount of named exports in one and the same file.

When importing named exports, you can also import all **named exports** at once with the following syntax:
```javascript
import * as upToYou from './path/to/file.js'; 
```