---
date: "2020-01-04"
description: ''
title: React JS como usar o useComponentDidMount
tags: hooks,effect,beginner
---

A hook that executes a callback immediately after a component is mounted.

- Use `React.useEffect()` with an empty array as the second argument to execute the provided callback only once when the component is mounted.

```jsx
const useComponentDidMount = onMountHandler => {
  React.useEffect(() => {
    onMountHandler()
  }, []);
}
```

```jsx
const Mounter = () => {
  useComponentDidMount(() => console.log('Component did mount'));

  return <div>Check the console!</div>;
}

ReactDOM.render(<Mounter />, document.getElementById('root'));
```
[Acesse a Referência original](http://github.com/30-seconds/)
