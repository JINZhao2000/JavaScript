# JavaScript

## 1. JavaScript 位置

- head 引入

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>js01</title>
      <script src="js01.js"></script>
  </head>
  <body>
  </body>
  </html>
  ```

- body 内部

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>js01</title>
  </head>
  <body>
      <h1>text</h1>
      <p>text</p>
      <script src="js01.js"></script>
  </body>
  </html>
  ```

## 2. JavaScript 基础语法

- 注释

  ```js
  // comments
  /* comments */
  ```

- 变量定义

  ```js
  var a = 'hello';
  var a = 1, b = 2, c = 3;
  var a = b = c = 4;
  typeof a; // number
  let a = 1; // tdc -> use after declaration
  const a = 1; // use after declaration
  ```

- 块作用域

  var 无块作用域，只有函数作用域，会污染变量

  ```js
  var i = 99;
  for (var i = 0; i<5; i++){
      ...;
  }
  console.log(i); // 5
  ```

  let 有块作用域，可以防止污染（const 也有块作用域）

  ```js
  var i = 99;
  for (let i = 0; i<5; i++){
      ...;
  }
  console.log(i); // 99
  ```

  window 作用域

  ```js
  var screenLeft = 10;
  console.log(window.screenLeft); // 10
  /* ------- */
  let screenLeft = 10;
  console.log(window.screenLeft); // suitable by window
  ```

  let 和 const 有重复声明报错

  Object.freeze(arg) 去锁定一个类不允许更改

  ```js
  const Obj = {
      field1: 'a'
  };
  Object.freeze(Obj);
  ```

- 传值与传址

  ```js
  let a = 1;
  let b = a;
  /* -------- */
  let e = {};
  let f = e;
  ```

- null 与 undefined

  ```js
  let a = null; // reference
  let b = undefined;
  ```

- 严格模式（作用域：当前作用域及其子作用域）

  ```js
  "use strict";
  ```

- for in / for of

  ```js
  for(let key in obj){}
  for(const iterator of obj){}
  ```

## 3. JavaScript 对象

- 类的判断

  ```js
  a instanceof b;
  ```

- String

  ```js
  let a = new String("a");
  console.log(a.toString()); // a
  /* ---------- */
  let a = 'a';
  console.log(a); // a
  /* ----------- */
  let a = "a";
  let b = "b";
  console.log(a+"something"+b);
  console.log(`${a}something${b}`);
  /* ----------- */
  function show(){
      return "a";
  }
  console.log(`letter{show()}`);
  ```

  用``拼接字符串，模板

  ```js
  let exemple = [
  	{title: "a"},
  	{title: "b"},
  	{title: "c"}
  ];
  function template(){
  	return `
  		<ul>${exemple.map((item)=>
  		`<li>${item.title}</li>`).join("")}</ul>
  		`;
  	}
  document.write(template());
  ```

  

