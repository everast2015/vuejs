## vuejs 的核心技术

## vuejs 的生命周期

1. created()

页面初始化数据的时候，加载的，例如，我们首次进来，请求后台的数据的时候，那就需要在此生命周期方法中，进行数据的请求，具体的操作如下：

```js

created() {
    this.$axios.get.call(this,this.url,parama).then((res) => {
        console.log('数据请求成功')
    })
}

```

2. mounted()

dom节点挂载的时候执行，如果我们的DOM节点开始加载的时候，加载完成之后，如果想要操作DOM的话，那么最合适的地方就是在，mounted()钩子函数中

```js

mounted() {
    // 获取DOM节点，或者操作DOM都可以
}

```

3. 解除绑定销毁子组件以及事件监听器

```js
destory() {
    // 解除绑定销毁子组件以及事件监听器
}

```

## vuejs 源码分析

1. 数据代理
2. 模板解析
3. 数据绑定

## axios 实现token 拦截

```js
// main.js 中
import axios from 'axios'

axios.prototype.$http = axios; // 将其放在原型链上，后续页面中，可以直接访问，this.$http

// 具体的请求的方法
methods: {
    getUsername() {
        let params = {
            username: this.username,
            pwd: this.pwd, // 默认data中的数据
        }
        this.$http.get(this.url, parama).then((res) => {
            console.log('数据请求成功')
        }),err => {
            console.log('数据请求失败')
        }
    }
}


// http.js 方法

import axios from 'axios';
import router from './router.js'

axios.interceptors.request.use(
    config=> {
        if(localstorage.token) {
            config.headers.authorization = localstorage.token // 从缓存中拿到token
        }
    }
)
```

