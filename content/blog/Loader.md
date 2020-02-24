---
date: "2020-01-04"
description: ''
title: React JS como usar o Loader
tags: visual,beginner
---

Creates a spinning loader component.

- Define appropriate CSS styles and animations for the component's elements.
- Define the component, which returns a simple SVG, whose size is determined by the `size` prop.

```css
.loader {
  animation: rotate 2s linear infinite;
}

@keyframes rotate {
  100% {
    transform: rotate(360deg);
  }
}

.loader circle {
  animation: dash 1.5s ease-in-out infinite;
}

@keyframes dash {
  0% {
    stroke-dasharray: 1, 150;
    stroke-dashoffset: 0;
  }
  50% {
    stroke-dasharray: 90, 150;
    stroke-dashoffset: -35;
  }
  100% {
    stroke-dasharray: 90, 150;
    stroke-dashoffset: -124;
  }
}
```

```jsx
function Loader({ size }) {
  return (
    <svg
      className="loader"
      xmlns="http://www.w3.org/2000/svg"
      width={size}
      height={size}
      viewBox="0 0 24 24"
      fill="none"
      stroke="currentColor"
      strokeWidth="2"
      strokeLinecap="round"
      strokeLinejoin="round"
    >
      <circle cx="12" cy="12" r="10" />
    </svg>
  );
}
```

```jsx
ReactDOM.render(<Loader size={24} />, document.getElementById('root'));
```
[Acesse a Referência original](http://github.com/30-seconds/)
