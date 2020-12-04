

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

## 3. JavaScript 基础数据类型

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

  标签模板
  
  ```js
  function baliseTemplate(strings, ... vars){
      strings.map((str,key)=>{
          return str+(vars[key]
                      ?vars[key].replace("a",`...`)
                      :"";
      }).join("");
  }
  ```
  
  字符串函数
  
  ```js
  let a = "abc";
  a.length; // 3
  a.toUpperCase(); // ABC
  a.toLowerCase(); // abc
  a.trim(); // delete space
  a.charAt(0); // a
  /* ------ */
  a.slice(1); // bc
  a.substr(1); // bc
  a.substring(1); // bc
  
  a.slice(1,2); // b
  a.substr(1,2); // bc 2 -> two number after a[1]
  a.substring(1,2); // b
  
  a.slice(-1); // c
  a.substr(-1); // c
  a.substring(-1); // abc <0 -> useless
  
  a.slice(-3,-2); // a
  a.substr(-3,2); // ab
  a.substring(-3,-2); // (nothing)
  /* ------ */
  let b = "abcabc";
  b.indexOf("a"); // 0
  b.indexOf("a",1); // 3  1 -> beginning position
  b.indexOf("d"); // -1
  b.lastIndexOf("a") // 3
  b.lastIndexOf("a",2) // 0
  b.includes("a"); // true
  b.includes("a",4) // false  4 -> beginning position
  b.startsWith("a") // true
  b.endsWith("c") // true
  b.replace("abc","d"); // dd
  ```
  
- 类型转换

  ```js
  const str = "99";
  typeof str; // str
  str + 78; // 9978
  str*1 + 78; // 177
  Number(str); + 88; // 187
  /* ---- */
  const num = 66;
  typeof num; // number
  num + ""; // "66" (string)
  String(num); // "66"
  /* ---- */
  const str2 = "99abc";
  parseInt(str2) // 99;
  /* ---- */
  const strarray = ["ab", "cd"];
  strarray.join("|"); // ab|cd
  /* ---- */
  const str3 = "abc";
  str3.split(""); // ["a","b","c"]
  /* ---- */
  const str4 = "abc"; // string
  const str5 = new String("abc"); // object
  ```

- 布尔类型

  ```js
  const bool = new Boolean(true); // object
  bool.valueOf(); // true
  /* ---- */
  let bool1 = true;
  typeof bool1; // boolean
  /* ---- */
  let num1 = 0;
  typeof num1; // number
  num1 = !!num1; // false
  /* ---- */
  let num2 = 0;
  Boolean(num2); // false
  /* ---- */
  let str1 = 'a';
  !!str1; // true
  Boolean(str1); // true
  /* ---- */
  let arr1 = [];
  !!arr1; // true
  Boolean(arr1); // true
  let obj = {};
  !!obj; // true
  Boolean(obj); // true
  ```

- Number

  ```js
  let num1 = new Number(1);
  typeof num1; // object
  num1.valueOf(); // 1
  num1.toString(); // "1"
  num1.isInteger(); // true
  let num2 = 1.999;
  num2.toFixed(2); // 1.99
  /* ---- */
  // NaN : not a number
  Number.isNaN(num2); // false
  Object.is(num2,NaN); // false
  /* ---- */
  Number(true); // 1
  Number(false); // 0
  Number("1"); // 1
  Number(parseInt("123abc")); // 123
  Number(parseFloat("123.123abc")); // 123.123
  Number([1]); // 1
  Number([1, 2]); // NaN
  Number({valueOf:function(){return 1;}}) // 1
  Number({}); // NaN
  ```

- Math

  ```js
  Math.max(1,2,3); // 3
  Math.min(1,2,3); // 1
  let arr1 = [1,2,3,4];
  Math.max.apply(null,arr1); // 4
  Math.ceil(2.1); // 3
  Math.floor(2.7); // 2
  Math.round(2.4); // 2
  Math.round(2.5); // 3
  (2.4234).toFixed(2) // 2.42
  Math.random(); // [0,1)
  Math.floor(Math.random()*11); // {0,1,2,3,4,5,6,7,8,9,10}
  ```

- Date

  ```js
  const date1 = new Date(); // object
  const date2 = Date(); // string
  date1*1; // millisecond
  date2*1; // NaN
  date2.now(); // millisecond
  Number(date1); // millisecond
  date1.valueOf(); // millisecond
  date1.getTime(); // millisecond
  date1.getFullYear(); // YYYY
  date1.getMonth(); // MM-1
  date1.getDate(); // DD
  date1.getHours(); // hh
  date1.getMinutes(); // mm
  date1.getSecondes(); // ss
  /* ---- */
  console.time("for") // flag name
  for (let i = 0; i < 20000; i++){}
  console.timeEnd("for")
  /* ---- */
  const date3 = new Date("2000-1-1 0:00:00");
  date.getMonth(); // 0
  const date4 = new Date("2000,1,1,0,00,00");
  const arr1 = [2000,1,1,0,00,00];
  const date5 = new Date(...arr1);
  /* ---- */
  const time1 = 10000000;
  new Date(time1);
  /* ---- */
  function dateFormat1(date1, format="YYYY-MM-DD HH:mm:ss"){
      config{
          YYYY : date1.getFullYear(),
  		MM : date1.getMonth()+1,
  		DD : date1.getDate(),
  		HH : date1.getHours(),
  		mm : date1.getMinutes(),
  		ss : date1.getSecondes()
      };
      for (const key in config){
          format = format.replace(key,config[key]);
      }
      return format;
  }
  /* ---- */
  // moment.js
  // npm install moment
  // var moment = require("moment");
  moment().format("YYYY-MM-DD HH:mm:ss");
  moment("2000-01-01 00:00:00").format("YYYY-MM-DD HH:mm:ss");
  moment("2000-01-01 00:00:00").add(10,"days"); // 2000-01-11
  ```

## 4. JavaScript 数组

- 数组创建

  ```js
  const arr1 = new Array("1",1); // object
  const arr4 = new Array(3); // [undefined, undefined,undefined] 
  const arr5 = Array.of(3); // [3]
  arr1.join("|"); // "1"|1
  let arr2 = [1,2,3];
  let arr3 = [["a"],["b"]];
  ```

- 数组使用

  ```js
  const arr1 = [1,2,3];
  arr1.length; // 3
  arr1.toString(); // 1,2,3
  arr1.join("|") // 1|2|3
  let str = "abcd";
  str.split(""); // ["a","b","c","d"]
  let str1 = "a,b,c,d";
  str1.split(","); // ["a","b","c","d"]
  Array.from(str); // ["a","b","c","d"]
  let obj{
      0: "A",
      1: "B",
      length: 2 // require else it will be []
  };
  Array.from(obj); // ["A","B"]
  let arr2 = ["A","B"];
  let arr3 = ["C","D"];
  for (const value of arr3){
      arr2.push(value);
  } // ["A","B","C","D"]
  arr2 = [...arr2,...arr3]; // ["A","B","C","D"]
  function sum(...args){
      args.reduce((s,v)=>{
          return (s+=v);
      },0);
  }
  /* ---- */
  let arr4 = ["a",1];
  let [letter,num] = arr4;
  let [,num2] = arr4;
  let [letter2,num3,other = 'other'] = arr4;
  let [letter3, ...args] = arr4;
  ```

- 管理数组元素

  ```js
  let arr1 = ["a","b"];
  arr1[aar1.length] = "c";
  let arr2 = ["d","e"];
  arr1 = [...arr1, ...arr2];
  arr1.push("f","g"); // at end
  arr1.pop(); // at end
  arr1.unshift("a"); // at begin
  arr1.shift(); // at begin
  arr1.fill("content",1,2); // content begin end
  /* ---- */
  let arr3 = [1,2,3,4,5];
  arr3.slice(1,2); // 2
  arr3.slice(); // 1,2,3,4,5
  arr3.slice(1); // 2,3,4,5
  arr3.splice(0,2) // 3,4,5 change the orignal array
  arr3.splice(0,2,"a") // "a",3,4,5
  arr3.length = 0; // clear
  /* ---- */
  let str = "a,b,c";
  let arr4 = str.split(","); // [a,b,c]
  arr4.join("-"); // a-b-c
  let arr5 = [1,2,3,4];
  arr4 = arr4.concat(arr5); // a,b,c,1,2,3,4
  arr4.copyWithin(2,0,3); // c -> a,b,c = a,b,a,b,c,3,4
  ```

- 查找

  ```js
  let arr1 = [1,2,3,4,2];
  arr1.indexOf(2); // 1
  arr1.indexOf(5); // -1
  arr1.lastIndexOf(2); // 4
  arr1.includes(1); // true
  arr1.indexOf(2,3); // 4
  arr1.lastIndexOf(2,-2); // 1
  arr1.find(function(item){
      console.log(item); // 1 | 2 | 3 | 4 | 5 
  });
  let objs = [
      {
          name: "a";
      },
      {
          name: "b";
      },
      {
          name: "c";
      }
  ];
  objs.includes({name: "b"};); // false
  objs.find(function(item){
      return item.name = "b";
  }); // true
  objs.findIndex(function(item){
      return item.name = "b";
  }); // 1
  objs.forEach(function(item){
      console.log(item);
  }); 
  ```

- 排序

  ```js
  let arr1 = [3,1,7,2,5];
  arr = arr.sort(function(a,b){
      return (a-b);
  }); // 1,2,3,5,7 b-a -> 7,5,3,2,1
  ```

- 迭代数组

  ```js
  // for value of arr - iterator
  // for i .. i.. i..
  // for key in arr - index
  // arr.forEach
  arr.keys(); // Iterator index done
  keys.next(); // value -> index done -> notHasNext
  arr.values(); // Iterator value done
  arr.entries(); // Iterator array done
  ```

- 处理数组

  ```js
  let arr1 = ["a","b"];
  arr1.every(function(item){
     return true;
  }); // all true => true 
  arr1.some ... ; // all false => false
  arr1.filter(function(value,index,arr){
      return true;
  }) // true => retain false => remove new arr
  /* ---- */
  arr1.map(function(value,index,arr){
      return "c";
  }); // ["c","c"] new arr
  /* ---- */
  let arr2 = [1,2,3,4,5];
  arr2.reduce(function(pre,value,index,array){
      console.log(pre,value);
      return 99; // pre => 1 99 99 99 99
  },0); // 0 => pre 0 99 99 99 99
  /* ---- */
  let arr3 = [1,2,3,4,3,2,4,2];
  let newArr = arr3.reduce(function(arr,cur){
      if(arr.includes(cur)===false){
          arr.push(cur);
      }
      return arr;
  },[]); // [1,2,3,4]
  ```

- Symbol

  ```js
  let a = Symbol(); // typeof : symbol
  let b = Symbol("description");
  let c = Symbol("description");
  b == c; // false
  b.description; // "description"
  let d = Symbol.for("desc"); // global
  let e = Symbol.for("desc"); // global
  d == e; // true
  Symbol.keyFor("a"); // global
  /* ---- */
  let symbol = Symbol("a");
  let a = {
      name: "a",
      [symbol]: "b"
  }
  for (const key of Object.getOwnPropertySymbols(a)){
      console.log(key); // Symbol("a")
  }
  for (const key of Reflect.ownKeys(a)){
      console.log(key); // name, Symbol("a")
  }
  ```

- Set

  ```js
  let st1 = new Set([1,2,3,4]); // 1,2,3,4
  let st2 = new Set(); // []
  let st3 = new Set("abc"); // a,b,c === let st3 = new Set([..."abc"]);
  st1.size; // 4
  st1.has(1); // true
  st1.has("1"); // false
  st1.delete(1); // true
  st1.values(); // SetIterator value
  st1.clear(); // size = 0
  Array.from(st2); // [a,b,c]
  [...set]; // [a,b,c]
  /* ---- */
  st2.values(); // [a,b,c]
  st2.keys(); // [a,b,c]
  st2.entries(); // [a,b,c]
  st2.forEach(function(value,key,set){
      console.log(set); // a,b,c
  })
  for (const value of set){
      console.log(set); // a,b,c
  }
  ```

- WeakSet

  ```js
  new WeakSet("a"); // Error
  new WeakSet(["a","b"]); // Error
  new WeakSet().add(["a","b"]);
  // js01/js02.html
  ```

- Map

  ```js
  let mp = new Map();
  mp.set("key","value");
  mp.set(1,"value");
  mp.set(function(){},"value");
  mp.set({},"value");
  let mp2 = new Map([["key","value"],[...]...]);
  mp.get("key"); // value
  mp.delete(1); // true
  mp2.clear;
  mp.has({}); // true
  /* ---- */
  mp.keys();
  mp.values();
  mp.entries();
  for (const key of mp.keys(),mp.values()){}
  for (const [key,value] of mp.entries()){}
  mp.forEach((key,value)=>{});
  /* ---- */
  // js01/js03.html
  // js01/js04.html
  ```

- WeakMap

  ```js
  new WeakMap(); // referenced only
  // js01/js05.html
  ```


## 5. JavaScript 函数

- 函数声明

  ```js
  let fun1 = new Function('title','console(title)');
  fun1("a"); // "a"
  function fun2(title){
      console.log(title);
  } // not recommented
  fun2("a"); // "a"
  let a = fun3(title){
      console.log(title);
  };
  a("a"); // a
  ```

- this

  - 普通函数（包括回调函数）this -> windows
  - 方法，属性函数 this -> 父级对象
  - lambda 表达式中 this -> 父级对象

  ```js
  {
      ...
      fun:function(){
          ...
          const self = this;
          ...(function(){
              self; // obj
              this; // windows
          });
      },
      ...
  }
  ```

  - 改变 this

    ```js
    function User(name){
        this.name = name;
    }
    let userA = new User("A"); // User{name: "A"}
    let elem = {age: 12};
    User.call(elem,"B"); // param1: this, param2-N: constructor
    console.log(elem); // {age: 12, name: "B"}
    User.apply(elem); // param1: this, param2: array
    
    ```

  