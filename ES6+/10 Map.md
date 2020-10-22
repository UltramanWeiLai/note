# Map

一种新的数据结构和对象比较类似  
但是 Map 比对象更加强大  
Map 的 key 可以用对象
应用场景：
1. 使用到 object 的地方都可以使用 Map

## 声明

```
    const m1 = new Map()
    console.log(m1) // Map(0) {}

    const m2 = new Map([ ['key', 'value'] ])
    console.log(m1) // Map(1) { key => 'value' }
```

## 设置

使用 set() 方法，即可在 Map 里面添加数据  
set() 方法 也能修改 Map 里面数据的值

```
    const m1 = new Map()
    m1.set('key', 'value')
    console.log(m1) // Map(1) { key => 'value' }

    const m2 = new Map()
    const obj = { name: 'Tiga' }
    m2.set(obj, 'value')
    console.log(m2) // Map(1) { {...} => 'value' }

    const m3 = new Map([ ['key', 'value'] ])
    m3.set('key', 'newValue')
    console.log(m3) // Map(1) { key => 'newValue' }
```
## 获取

使用 get() 方法，即可获取 Map 里面数据

```
    const m1 = new Map()
    m1.set('key', 'value')
    console.log(m1.get('key')) // value
```

## 删除

使用 deete() 方法，即可删除 Map 里面数据

```
    const m1 = new Map([ ['key', 'value'] ])
    m1.deete('key')
    console.log(m1) // Map(0) {}
```

## 查询


### 查询是否包含某个值

使用 has() 方法，可以判断 Map 里面是否有某个数据

```
    const m1 = new Map([ ['key', 'value'] ])
    console.log(m1.has('key')) // true
```

### 查询拥有多少条数据

使用 size() 方法，可以获取 Set 拥有多少条数据

```
    const m1 = new Map([ ['key', 'value'] ])
    console.log(m1.size) // 1
```
## 遍历

```
    const map = new Map([ ['key', 'value'] ])
    map.forEach((value, key) => {
        console.log(key, ':', value)
    })

    for( cosnt [key, value] of map) {
        console.log(key, ':', value)
    }

    for( cosnt key of map.keys()) {
        console.log(map[key])
    }

    for( cosnt value of map.values()) {
        console.log(value)
    }

    for( cosnt [key, value] of map.entries()) {
        console.log(key, ':', value)
    }
```

# WeakMap

WeakMap 的 key 只能用 引用类型
WeakMap 的方法和 Map 类似

1. set
2. get
3. delete
4. has

WeakMap 不能遍历  
WeakMap 是一种弱引用，这种引用是不记录垃圾回收机制的
