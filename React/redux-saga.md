#### Generator
```
function* gen() {
    console.log(1);
    yield;
    console.log(2);
    yield;
    console.log(3);
    yield 4;
}

const generator = gen();
generator.next(); // 1 {value: undefined, done: false}
generator.next(); // 2 {value: undefined, done: false}
generator.next(); // 3 {value: 4, done: false}
generator.next(); // {value: undefined, done: true}
generator.next(); // {value: undefined, done: true}
...

```

#### Generator watch
```
function* watchGen() {
    while(true) {
        const action = yield;
        if (action.type === 'START') {
            console.log('start');
        }
        if (action.type === 'END') {
            console.log('end');
        }
    }
}

const watch = watchGen();
watch.next({type: 'START'}) // start
watch.next({type: 'END'}) // end
```