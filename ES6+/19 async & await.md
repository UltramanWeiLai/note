# async/await

async/await 其实就是 Generator 和 Promise 的语法糖
主要就是达成 伪同步 代码

```
    async function foo () {
        const res = await ajax('api/api')
    }
```

## 异步迭代

### for-await-of

```
    async function test() {
        for await ( let item of ajaxs) {
            console.log(item)
        }
    }
```

### Symbol.asyncIterator

```
    const arr = [ajax1(), ajax2()]
    arr[Symbol.asyncIterator] = function() {
        const index = 0
        return {
            next() {
                return index < this.length
                    ? {
                        value: this[index++],
                        done: false
                    }
                    : {
                        value: undefined,
                        done: true
                    }
            }
        }
    }
```

