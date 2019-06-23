#### 语法

> Object.assign(target, …sources)

#### 描述

如果目标对象的属性具有相同的键，则***目标对象的属性被源对象的属性覆盖***。后面源对象的属性将类似地覆盖前面源对象的属性。

```js
let target = { name: 'js' };
const source1 = { name: 'JS', age: 10 };
const source2 = { name: 'Javascript', age: 15 };
target = Object.assign(target, source1, source2); // {name: "Javascript", age: 15}
```



`Object.assign`方法只会拷贝源对象***自身的并且可枚举的***属性到目标对象。

```js
const obj = Object.create({foo: 1}, { // foo 是个继承属性
  bar: {
    value: 2, // bar 是个不可枚举属性
  },
  baz: {
    value: 3,
    enumerable: true // baz 是个自身并且可枚举的属性
  }
})

const copy = Object.assign({}, obj);
console.log(copy); // {baz: 3}
```



***复合属性***会被全部覆盖

```js
const source1 = {
  name: 'source1',
  book: {
		name: 'Java',
    age: 10,
  },
};
const source2 = {
  name: 'source2',
  book: {
		name: 'Javascript',
  },
}

const bookObj = Object.assign({}, source1, source2); 
console.log(bookObj.book); // {name: 'Javascript'}
```

