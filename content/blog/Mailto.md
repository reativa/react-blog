---
date: "2020-01-04"
description: ''
title: React JS como usar o Mailto
tags: visual,beginner
---

Renders a link formatted to send an email.

- Destructure the component's props, use `email`, `subject` and `body` to create a `<a>` element with an appropriate `href` attribute.
- Render the link with `props.children` as its content.

```jsx
function Mailto({ email, subject, body, ...props }) {
  return (
    <a href={`mailto:${email}?subject=${encodeURIComponent(subject) || ''}&body=${encodeURIComponent(body) || ''}`}>{props.children}</a>
  );
}
```

```jsx
ReactDOM.render(
  <Mailto email="foo@bar.baz" subject="Hello & Welcome" body="Hello world!">
    Mail me!
  </Mailto>,
  document.getElementById('root')
);
```
[Acesse a Referência original](http://github.com/30-seconds/)
