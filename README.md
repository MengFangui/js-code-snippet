## 判断对象是否含有某个属性（自身属性，非继承属性）

``` javascript
const has = Object.prototype.hasOwnProperty;
console.log(has.call(object, key));
```

## 对象浅拷贝

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

## 数组拷贝

``` javascript
// bad
const len = items.length;
const itemsCopy = [];
let i;

for (i = 0; i < len; i += 1) {
  itemsCopy[i] = items[i];
}

// good
const itemsCopy = [...items];
```

## 可迭代对象转换为数组

``` javascript
const foo = document.querySelectorAll('.foo');

// good
const nodes = Array.from(foo);

// best
const nodes = [...foo];
```

## 函数参数（不要使用arguments）

``` javascript
// bad
function concatenateAll() {
  const args = Array.prototype.slice.call(arguments);
  return args.join('');
}

// good
function concatenateAll(...args) {
  return args.join('');
}
```

## 函数参数默认值

``` javascript
// really bad
function handleThings(opts) {
  // No! We shouldn’t mutate function arguments.
  // Double bad: if opts is falsy it'll be set to an object which may
  // be what you want but it can introduce subtle bugs.
  opts = opts || {};
  // ...
}

// still bad
function handleThings(opts) {
  if (opts === void 0) {
    opts = {};
  }
  // ...
}

// good
function handleThings(opts = {}) {
  // ...
}
```

