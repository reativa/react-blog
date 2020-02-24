---
date: "2020-01-04"
description: ''
title: React JS como usar o TextArea
tags: input,beginner
---

Renders a `<textarea>` element that uses a callback function to pass its value to the parent component.

- Use object destructuring to set defaults for certain attributes of the `<textarea>` element.
- Render a `<textarea>` element with the appropriate attributes and use the `callback` function in the `onChange` event to pass the value of the textarea to the parent.

```jsx
function TextArea({
  callback,
  cols = 20,
  rows = 2,
  disabled = false,
  readOnly = false,
  placeholder = ''
}) {
  return (
    <textarea
      cols={cols}
      rows={rows}
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
  <TextArea placeholder="Insert some text here..." callback={val => console.log(val)} />,
  document.getElementById('root')
);
```
[Acesse a Referência original](http://github.com/30-seconds/)
