 #### 1、不允许在末尾添加多余的逗号

```javascript
JSON.parse('[1, 2,3,]') // SyntaxError
JSON.parse('{"age": 12,}') // SyntaxError

JSON.parse('{"age": 12}') // {age: 12}
```



#### 2、属性名必须使用单引号

```javascript
JSON.parse('{'age': 18}') // SyntaxError

JSON.parse('{"age": 18}') // {age: 18}
```



#### 3、前导0和小数点（针对数字）

>数值类型：不能用 0 开头，小数点后面必须包含一位数字

```javascript
JSON.parse('{"age": 012}') // SyntaxError
JSON.parse('12.')  // SyntaxError

JSON.parse('12') // 12
// 注意：JSON.stringify 支持以 0 开头，但会以 八进制来处理
JSON.stringify(012) // "10"
```

