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