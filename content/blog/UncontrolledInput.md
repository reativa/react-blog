---
date: "2020-01-04"
description: ''
title: React JS como usar o UncontrolledInput
tags: input,beginner
---

Renders an `<input>` element that uses a callback function to pass its value to the parent component.

- Use object destructuring to set defaults for certain attributes of the `<input>` element.
- Render an `<input>` element with the appropriate attributes and use the `callback` function in the `onChange` event to pass the value of the input to the parent.

```jsx
function UncontrolledInput({
  callback,
  type = 'text',
  disabled = false,
  readOnly = false,
  placeholder = ''
}) {
  return (
    <input
      type={type}
      disabled={disabled}
      readOnly={readOnly}
      placeholder={placeholder}
      onChange={({ target: { value } }) => callback(value)}
    />
  );
}
```

```jsx
ReactDOM.render(
  <UncontrolledInput
    type="text"
    placeholder="Insert some text here..."
    callback={val => console.log(val)}
  />,
  document.getElementById('root')
);
```
[Acesse a Referência original](http://github.com/30-seconds/)
