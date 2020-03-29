## 判断对象是否含有某个属性（自身属性，非继承属性）

``` javascript
const has = Object.prototype.hasOwnProperty;
console.log(has.call(object, key));
```

