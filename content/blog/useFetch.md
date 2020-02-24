---
date: "2020-01-04"
description: ''
title: React JS como usar o useFetch
tags: hooks,effect,state,intermediate
---

A hook that implements `fetch` in a declarative manner.

- Create a custom hook that takes a `url` and `options`.
- Use the `React.useState()` hook to initialize the `response` and `error` state variables.
- Use the `React.useEffect()` hook to anychronously call `fetch()` and update the state varaibles accordingly.
- Return an object containting the `response` and `error` state variables.

```jsx
const useFetch = (url, options) => {
  const [response, setResponse] = React.useState(null);
  const [error, setError] = React.useState(null);

  React.useEffect(() => {
    const fetchData = async () => {
      try {
        const res = await fetch(url, options);
        const json = await res.json();
        setResponse(json);
      } catch (error) {
        setError(error);
      }
    };
    fetchData();
  }, []);

  return { response, error };
};
```

```jsx
const ImageFetch = props => {
  const res = useFetch('https://dog.ceo/api/breeds/image/random', {});
  if (!res.response) {
    return <div>Loading...</div>;
  }
  const imageUrl = res.response.message;
  return (
    <div>
      <img src={imageUrl} alt="avatar" width={400} height="auto" />
    </div>
  );
};

ReactDOM.render(<ImageFetch />, document.getElementById('root'));
```
[Acesse a Referência original](http://github.com/30-seconds/)
