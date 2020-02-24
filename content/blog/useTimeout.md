---
date: "2020-01-04"
description: ''
title: React JS como usar o useTimeout
tags: hooks,effect,intermediate
---

A hook that implements `setTimeout` in a declarative manner.

- Create a custom hook that takes a `callback` and a `delay`.
- Use the `React.useRef()` hook to create a `ref` for the callback function.
- Use the `React.useEffect()` hook to remember the latest callback.
- Use the `React.useEffect()` hook to set up the timeout and clean up.

```jsx
const useTimeout = (callback, delay) => {
  const savedCallback = React.useRef();

  React.useEffect(() => {
    savedCallback.current = callback;
  }, [callback]);

  React.useEffect(() => {
    function tick() {
      savedCallback.current();
    }
    if (delay !== null) {
      let id = setTimeout(tick, delay);
      return () => clearTimeout(id);
    }
  }, [delay]);
};
```

```jsx
const OneSecondTimer = props => {
  const [seconds, setSeconds] = React.useState(0);
  useTimeout(() => {
    setSeconds(seconds + 1);
  }, 1000);

  return <p>{seconds}</p>;
};

ReactDOM.render(<OneSecondTimer />, document.getElementById('root'));
```
[Acesse a Referência original](http://github.com/30-seconds/)
