# React学习笔记

* React

* registServiceWorker离线缓存，只在生产环境有效

- 注册：register方法是默认（default）的导出方法。

```js
    export default function register() {
  //当前环境是生产环境并且浏览器支持serverWorker
  // The URL constructor is available in all browsers that support SW.
  if (process.env.NODE_ENV === 'production' && 'serviceWorker' in navigator) {
    //返回一个新的URL，作为生成静态文件夹的路径，下面说明...
    const publicUrl = new URL(process.env.PUBLIC_URL, window.location);
    //如果静态文件和当前环境不在同一个域，注册没有意义，那就直接返回。
    if (publicUrl.origin !== window.location.origin) {
      return;
    }
   
    window.addEventListener('load', () => {
      //页面加载完成执行以下代码....
      const swUrl = `${process.env.PUBLIC_URL}/service-worker.js`;
      if (isLocalhost) {
        // 如果是本地环境，调用checkValidServiceWorker进行注册
        checkValidServiceWorker(swUrl);
        // 注册成功后，打印信息
        navigator.serviceWorker.ready.then(() => {
          console.log(
            'This web app is being served cache-first by a service ' +
              'worker. To learn more, visit https://goo.gl/SC7cgQ'
          );
        });
      } else {
        // 如果不是本地环境（已经暴露在外网）仅仅只注册 service worker
        registerValidSW(swUrl);
      }
    });
  }
}

```

- `unregister()`取消注册

```js
    export function unregister() {
        if ('serviceWorker' in navigator) {
            navigator.serviceWorker.ready.then(registration => {
            registration.unregister();
            });
        }
    }

```

- 注册有效的serviceWorker

- 判断serviceWorker状态