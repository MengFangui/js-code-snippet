## 判断对象是否含有某个属性（自身属性，非继承属性）

``` javascript
const has = Object.prototype.hasOwnProperty;
console.log(has.call(object, key));
```

## 浅拷贝

``` javascript
// bad
const original = {
  a: 1,
  b: 2
};
const copy = Object.assign({}, original, {
  c: 3
}); // copy => { a: 1, b: 2, c: 3 }

// good
const original = {
  a: 1,
  b: 2
};
const copy = {
  ...original,
  c: 3
}; // copy => { a: 1, b: 2, c: 3 }

//获取一些属性
const {
  a,
  ...noA
} = copy; // noA => { b: 2, c: 3 }
```

