# 学习JavaScript笔记

* 这几篇，应该还算比较全面了[you don't know js](https://github.com/GuangDongNO1/you-dont-know-js)

## 重点

* 基本类型
    - 基础类型(栈中)
    `String`,`Number`,`Boolean`, `null`, `undefined`
    - 引用类型(堆中)
    `Object`,`Array`,`Function`

* 原型和原型链

* 作用域和闭包

* 垃圾回收机制

## 面试题

- 循环异步问题
```js
    var input = document.querySelectorAll('input'); // input.length = 5
    for (var i = 0; i < 5; i++) {
        setTimeout(()=>{
            console.log(i) // 5,5,5,5,5
        })
    }

    // 解决

    // 闭包 
    for (var i = 0; i < input.length; i++) {
        ~function(i){
            setTimeout(()=>{
                console.log(i) // 0,1,2,3,4
            })
        }(i)
    }

    // 保存新属性
    for (var i = 0; i < input.length; i++) {
        input[i].myIndex = i;
            setTimeout(()=>{
                console.log(input[i].myIndex); // 0,1,2,3,4
            })
        }(i)
    }

    // let（块级作用域）
    for (let i = 0; i < input.length; i++) {
        setTimeout(()=>{
            console.log(i)// 0,1,2,3,4
        })
    }
```

- this问题

```javascript
    var name = 'window';
    var obj = {
        name: 'obj',
        foo: {
            getName:function(){
               return this.name;
            }
        }
    }
    console.log(obj.foo.getName()); // undefined
    var foo = obj.foo.getName;
    console.log(foo()); // window
```

- 原型链

```js

```

- 闭包

```js
    // 数组去重
    (function(){
        Array.prototype.myDistinct = function(){
            var obj = {};
            for(var i=0;i<this.length;i++){
                var item = this[i];
                if(typeof obj[item]!=='undefined'){
                    this[i] = this[this.length - 1];
                    this.length --;
                    i--;
                    continue;
                }
                obj[item] = item;
            }
            obj = null;
            return this;
        }
    })()
```


