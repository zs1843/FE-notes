# ES6 学习笔记

* ES6是JavaScript的语法糖，写法上当然有很多便利。

## async/await

* async配合await写起来绝对的简洁啊

- 来一段promise常规写法

```js
  const a = new Promise((resolve, reject)=>{
       setTimeout(() => {
             resolve(str)
       }, 1000);
  });
  a.then((res)=>{
      console.log(res)
  }).catch(e=>{
      console.log(e.message)
  })
  // promise嵌套
  const p1 = new Promise((resolve, reject)=>{
      resolve(res1);
  })
  const p2 = new Promise((resolve, reject)=>{
      resolve(res2);
  })
  const p3 = new Promise((resolve, reject)=>{
      resolve(res3);
  })
  p3.then(res3=>{
      return p2;
  }).then(res2=>{
      return p1
  }).then(res1=>{
      console.log(res1);
  }).catch(e=>{
      console.log(e.message);
  })
```