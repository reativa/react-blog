---
date: "2020-01-04"
description: ''
title: React JS como usar o usePrevious
tags: hooks,state,effect,intermediate
---

A hook that stores the previous state or props.

- Create a custom hook that takes a `value`.
- Use the `React.useRef()` hook to create a `ref` for the `value`.
- Use the `React.useEffect()` hook to remember the latest `value`.

```jsx
const usePrevious = value => {
  const ref = React.useRef();
  React.useEffect(() => {
    ref.current = value;
  });
  return ref.current;
}
```

```jsx
const Counter = () => {
  const [value, setValue] = React.useState(0);
  const lastValue = usePrevious(value);
  
  return (
    <div>
      <p>Current: {value} - Previous: {lastValue}</p>
      <button onClick={() => setValue(value + 1)}>Increment</button>
    </div>
  );
};

ReactDOM.render(<Counter />, document.getElementById('root'));
```
[Acesse a Referência original](http://github.com/30-seconds/)
