---
date: "2020-01-04"
description: ''
title: React JS como usar o RippleButton
tags: visual,state,effect,intermediate
---

Renders a button that animates a ripple effect when clicked.

- Define some appropriate CSS styles and an animation for the ripple effect.
- Use the `React.useState()` hook to create appropriate variables and setters for the pointer's coordinates and for the animation state of the button.
- Use the `React.useEffect()` hook to change the state every time the `coords` state variable changes, starting the animation.
- Use `setTimeout()` in the previous hook to clear the animation after it's done playing.
- Use the `React.useEffect()` hook a second time to reset `coords` whenever the `isRippling` state variable is `false.`
- Handle the `onClick` event by updating the `coords` state variable and calling the passed callback.
- Finally, render a `<button>` with one or two `<span>` elements, setting the position of the `.ripple` element based on the `coords` state variable.

```css
.ripple-button {
  border-radius: 4px;
  border: none;
  margin: 8px;
  padding: 14px 24px;
  background: #1976d2;
  color: #fff;
  overflow: hidden;
  position: relative;
  cursor: pointer;
}

.ripple-button > .ripple {
  width: 20px;
  height: 20px;
  position: absolute;
  background: #63a4ff;
  display: block;
  content: "";
  border-radius: 9999px;
  opacity: 1;
  animation: 1.2s ease 1 forwards ripple-effect;
}

@keyframes ripple-effect {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  50% {
    transform: scale(10);
    opacity: 0.375;
  }
  100% {
    transform: scale(35);
    opacity: 0;
  }
}

.ripple-button > .content {
  position: relative;
  z-index: 2;
}

```

```jsx
function RippleButton({ children, onClick }) {
  const [coords, setCoords] = React.useState({ x: -1, y: -1 });
  const [isRippling, setIsRippling] = React.useState(false);

  React.useEffect(
    () => {
      if (coords.x !== -1 && coords.y !== -1) {
        setIsRippling(true);
        setTimeout(() => setIsRippling(false), 1200);
      } else setIsRippling(false);
    },
    [coords]
  );

  React.useEffect(
    () => {
      if (!isRippling) setCoords({ x: -1, y: -1 });
    },
    [isRippling]
  );

  return (
    <button
      className="ripple-button"
      onClick={e => {
        var rect = e.target.getBoundingClientRect();
        var x = e.clientX - rect.left;
        var y = e.clientY - rect.top;
        setCoords({ x, y });
        onClick && onClick(e);
      }}
    >
      {isRippling ? (
        <span
          className="ripple"
          style={{
            left: coords.x + 10,
            top: coords.y
          }}
        />
      ) : (
        ""
      )}
      <span className="content">{children}</span>
    </button>
  );
}
```

```jsx
ReactDOM.render(
  <RippleButton onClick={e => console.log(e)}>Click me</RippleButton>,
  document.getElementById('root')
);
```
[Acesse a Referência original](http://github.com/30-seconds/)
