### ScrollTrigger
```
ScrollTrigger.create({
  animation: timeline,
  trigger: triggerSelector,
  toggleActions: 'play pause resume pause',
  start: 'top bottom',
  end: "10%",
  markers: false,
  anticipatePin: 1,
});
```

### Draggable + HitTest
```
Draggable.create(dragSelector, {
  type: 'x, y',
  bounds: $('#scene3_2 .pattern_wrap_1'),
  edgeResistance: 0.75,
  onDragStart: function () {
    ...
  },
  onDrag: function () {
    if (this.hitTest(dropSelector, 75)) {
      // hit effect on
    } else {
      // hit effect off
    }
  },
  onDragEnd: function () {
    if (this.hitTest(dropSelector, 75)) {
      ...
    } else {
      TweenLite.to(this.target, 0.3, { x: 0, y: 0, opacity: 1 }); // revert
    }
  },
});
```

### Stagger
```
TimelineMax.staggerFromTo(arraySelector, 0.4, { opacity: 0 }, { opacity: 1 }, 0.1)
```
