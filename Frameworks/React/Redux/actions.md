## Actions

### Action Types (constants)

_actionTypes.js_

```js
export const A_ACTION_TYPE = "A_ACTION_TYPE";
export const B_ACTION_TYPE = "B_ACTION_TYPE";
```

### Action Creators

_aActions.js_

```js
import { A_ACTION_TYPE } from './actionTypes'

export const aAction = (val) => {
  type: A_ACTION_TYPE,
  payload: { val }
}
```

_bActions.js_

```js
import { B_ACTION_TYPE } from './actionTypes'

export const bAction = (val) => {
  type: B_ACTION_TYPE,
  payload: { val }
}
```
