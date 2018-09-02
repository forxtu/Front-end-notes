## Reducers

_rootReducer.js_ - to combine multiple reducers

```js
import { combineReducers } from "redux";

import aReducer from "./aReducer";
import bReducer from "./bReducer";

const rootReducer = combineReducers({
  a: aReducer,
  b: bReducer
});

export default rootReducer;
```

_aReducer.js_

```js
import { A_ACTION_TYPE } from "../actions/actionTypes";

const initialState = {
  a: "aaa"
};

export default (state = initialState, action) => {
  switch (action.type) {
    case A_ACTION_TYPE:
      return {
        ...state,
        a: action.payload.val
      };

    default:
      return state;
  }
};
```

_bReducer.js_

```js
import { B_ACTION_TYPE } from "../actions/actionTypes";

const initialState = {
  b: "bbb"
};

export default (state = initialState, action) => {
  switch (action.type) {
    case B_ACTION_TYPE:
      return {
        ...state,
        b: action.payload.val
      };

    default:
      return state;
  }
};
```
