# ES6 学习笔记

* ES6是JavaScript的语法糖，写法上当然有很多便利。

## async/await

* async配合await写起来绝对的简洁啊

- 来一段promise常规写法

```js
  const = a = () => new Promise((resolve, reject)=>{
      resolve()
  });
  a.then((res)=>{
      console.log(res)
  }).catch(e=>{
      console.log(e.message)
  })
    
```