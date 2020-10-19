##### Destructuring assignment & Template literals
```
const emsbn = {
    name: 'SB',
    birth: '1990.07.19',
    location: 'Hanam'
}

const { name, birth, location } = emsbn;
const info = `${name}은 ${birth}에 태어났고 ${location}에서 쭉 살았다.`  
```

##### Spread syntax
```
const emsbn2 = { ...emsbn, lastName: 'Lim' }

const emsbnArr = ['SB', '1990.07.19', 'Hanam']
const emsbnArr2 = [...emsbnArr, 'Lim']
```

##### Loop
```
const stocks = [
    { name: 'samsung', price: 60000 },
    { name: 'LG', price: 89000 },
    { name: 'SK', price: 86000 }
]

const total = stocks.reduce((acc, cur) => acc + cur.price, 0); // 235000 
const price = stocks.map((stock) => stock.price); // [ 60000, 89000, 86000 ]  
const filter = stocks.filter((stock) => stock.price > 80000); // [ { name: 'LG', price: 89000 }, { name: 'SK', price: 86000 } ] 
```

##### async / await
```
const random = () => {
    return Promise.resolve(Math.floor(Math.random()*11));
};
const randomCalc = async () => {
    const first = await random();
    const second = await random();
    const third = await random();
    
    return first + second + third;
};
randomCalc();
```
