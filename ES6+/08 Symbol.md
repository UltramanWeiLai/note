# Symbol 符号类型值

Symbol 是一种新的原始数据类型，是匿名的并且不可枚举
应用场景：
1. 有重复的 key 的时候
2. 一定程度上可以作为私有属性被保护，一般遍历是无法获取 Symbol 为 key 的属性的，但是 Reflect.ownKeys 和 Object.getOwnPropertySymbols 是可以获取的
3. 可以消除模糊字符串

## 声明

```
    const s1 = Symbol()
    console.log(s1) // Symbol()
    console.log(s1.description) // undefined

    const s2 = Symbol('foo')
    console.log(s2) // Symbol(foo)
    console.log(s2.description) // foo

    const s3 = Symbol({ name: 'Tiga' })
    console.log(s3) // Symbol([object Object]) 注：会自动调用 toString 来作为展示
    console.log(s3.description) // [object Object]

    const s4 = Symbol.for('foo')
    console.log(s4) // Symbol(foo)
    console.log(s4.description) // foo
```

## 判断

Symbol 表示为独一无二的，所以哪怕是长得一样它们也不相等

```
    // 定一个新的 Symbol
    const s1 = Symbol()
    const s2 = Symbol()
    console.log(s1 === s2) // false

    // Symbol.for 会在全局的Symbol上定义
    // 所以重复定义的时候会在全局的Symbol里面去找
    const s3 = Symbol.for('foo')
    const s4 = Symbol.for('foo')
    console.log(s3 === s4) // true 注：s3 和 s4 指向的内容其实是同一个
```

## 查询

可以通过 Symbol.keyFor() 来查询是否在全局的Symbol上登记过

```
    const s1 = Symbol('foo')
    console.log(Symbol.keyFor(s1)) // undefined

    const s2 = Symbol.for('foo')
    console.log(Symbol.keyFor(s2)) // foo
```
