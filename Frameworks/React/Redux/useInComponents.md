## How to use store in components

```js
import React, { Component } from "react";
import { string, func } from "prop-types";
import { connect } from "react-redux";

import { aAction } from "./store/actions/aActions";
import { bAction } from "./store/actions/bActions";

export class App extends Component {
  static propTypes = {
    a: string,
    b: string,
    aAction: func,
    bAction: func
  };

  render() {
    const { a, b, aAction, bAction } = this.props;
    return (
      <div>
        {a}
        {b}
        <button click={() => aAction("change a to c")}>change a</button>
        <button click={() => bAction("change b to d")}>change b</button>
      </div>
    );
  }
}

const mapStateToProps = state => ({
  a: state.a.a,
  b: state.b.b
});

const mapDispatchToProps = {
  aAction,
  bAction
};

export default connect(
  mapStateToProps,
  mapDispatchToProps
)(App);
```
