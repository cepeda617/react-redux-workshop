##Exercise 7: Add CSS to `Toggle`
1. Import the CSS in `app/styles/toggle.sass` into `Toggle`.
  ```jsx
  // app/components/Toggle.js
  import React, { Component, PropTypes } from 'react'
  import css from '../styles/toggle'
  ```

1. Assign `className` to rendered elements using classes declared in CSS.
  ```jsx
  // app/components/Toggle.js
  render() {
    return (
      <div className={css.control} onClick={this._handleClick}>
        <div className={css.toggle}>
          {this.state.enabled ? this.props.enabledText : this.props.disabledText}
        </div>
        <div className={css.label}>{this.props.children}</div>
      </div>
    )
  }
  ```
  That should make our `Toggle` pretty.

1. Use the `classnames` module to conditionally join classNames together. We'll use `classnames` to add the
`css.enabled` class next to `css.toggle` whenever `state.enabled` is `true`. Change `className={css.toggle}` to `className={classnames.bind(css)('toggle', { enabled: this.state.enabled })}`.
  ```jsx
  // app/components/Toggle.js
  import classnames from 'classnames/bind' // <-- ADD PACKAGE

  // ...
  render() {
    return (
      <div className={css.control} onClick={this._handleClick}>
        <div className={classnames.bind(css)('toggle', { enabled: this.state.enabled })}> {/* <-- CHANGE */}
          {this.state.enabled ? this.props.enabledText : this.props.disabledText}
        }
        </div>
        <div className={css.label}>{this.props.children}</div>
      </div>
    )
  }
  ```
  > **Note:** We're using CSS Modules, so the actual CSS class names are scoped locally by default. In this case, they're
  scoped to the `Toggle` component. For example, instead of `.toggle`, it looks more like `.app-styles-toggle---toggle---3l82H`.
  See https://github.com/css-modules/css-modules.

1. Your `Toggle` should now turn green when enabled.


<br>
###[Next Step: Create a `Settings` component using `Toggle` components &rarr;](./exercise-8.md)
