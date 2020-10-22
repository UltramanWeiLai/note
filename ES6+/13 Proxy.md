# Proxy 代理

具体还是看看 MDN 把，这玩意很强大啊！  
[Proxy](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy)

## 拦截

### ES5

ES5 中对数据做拦截的话用的是 Object.defineProperty()

```
    const obj = {}
    const name
    Object.defineProperty(obj, 'name', {
        get() {
            // ....
            return name
        }

        set(val) {
            name = val
        }
    })
```

### ES6

```
    const obj = {}
    cosnt p = new Proxy(obj, {})

    // get
    const arr = [1, 2, 3]
    arr = new Proxy(arr, {
        get(target, prop) {
            return prop in target ? target[prop] : 'error'
        }
    })

    // set
    const obj2 = {}
    obj2 = new Proxy(obj2, {
        set(target, prop, val) {
            target[prop] = val
        }
    })

    // has
    const obj3 = {}
    obj3 = new Proxy(obj3, {
        has(target, prop) {
            return target[prop] ? true : false
        }
    })

    // ownKeys 拦截循环
    const obj4 = {
        [Symbol('es')]: 'es'
    }

    obj4 = new Proxy(obj4, {
        ownKeys(target) {
            return Object.keys(target)
        }
    })
```
