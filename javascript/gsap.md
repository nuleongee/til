### ScrollTrigger
```
ScrollTrigger.create({
  animation: timeline,
  trigger: triggerSelector,
  toggleActions: 'play pause resume pause',
  start: 'top bottom',
  // end: "10%",
  markers: false,
  anticipatePin: 1,
});
```

### Draggable + HitTest
```
Draggable.create(dragSelector, {
  type: 'x, y',
  bounds: boundsSelector,
  edgeResistance: resistancePercent,
  onDragStart: function () {
    ...
  },
  onDrag: function () {
    if (this.hitTest(dropSelector, threshold)) {
      // hit effect on
    } else {
      // hit effect off
    }
  },
  onDragEnd: function () {
    if (this.hitTest(dropSelector, threshold)) {
      ...
    } else {
      TweenLite.to(this.target, 0.3, { x: 0, y: 0, opacity: 1 }); // revert
    }
  },
});
```

### Stagger
```
tween.staggerFromTo(arraySelector, time, { opacity: 0 }, { opacity: 1 }, staggerTime)
```

#### Scroll
```
tween.to(window, time, {
  scrollTo: { y: top, autoKill: true },
  ease: ease,
});
```
