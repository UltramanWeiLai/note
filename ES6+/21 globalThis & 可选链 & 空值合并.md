# globalThis 

提供了一种标砖的方式去获取不同环境下的全局对象

```
    console.log(globalThis)
```

# optional chaining 可选链

```
    const data = {
        a: {
            b: 'c'
        }
    }

    ES5
    const d1 = data && data.a && data.a.b

    ES11
    const d2 = data?.a?.b
```

# Nullish coalescing Operator 空值合并运算符

只有在当前两个问号前面的值为 null 和 undefined 的时候才获取后面的值

```
    const a = null ?? 6
    console.log(a) // 6

    const a = undefined ?? 6
    console.log(a) // 6

    const a = 0 ?? 6
    console.log(a) // 0

    const a = 10 ?? 6
    console.log(a) // 10

    const a = false ?? 6
    console.log(a) // false

    const a = true ?? 6
    console.log(a) // true
```