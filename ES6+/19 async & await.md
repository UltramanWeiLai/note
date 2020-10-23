# async/await

async/await 其实就是 Generator 和 Promise 的语法糖
主要就是达成 伪同步 代码

```
    async function foo () {
        const res = await ajax('api/api')
    }
```