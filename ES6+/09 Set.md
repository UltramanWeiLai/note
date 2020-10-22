# Set 集合

一种新的数据结构和数组比较类似，但是 Set 的值是唯一的  
Set 也有 key 和 value 只是 Set 的 key 和 value 是一样的
这么看来，其实 Set 也是哈希表，也就是对象、字典一类的东西，只是做了封装
应用场景：
1. 数组去重
2. 合并去重
3. 交集 注: 配合数组的filter
4. 差集 注: 配合数组的filter


## 声明

```
    const s1 = new Set()
    console.log(s1) // Set(0) {}

    const s2 = new Set([1, 2, 3])
    console.log(s2) // Set(3) {1, 2, 3}

    const s3 = new Set([1, 2, 3, 3, 3, 3])
    console.log(s3) // Set(3) {1, 2, 3}
```

## 添加

使用 add() 方法，即可在 Set 里面添加数据

```
    const s1 = new Set()
    console.log(s1) // Set(0) {}
    s1.add(1)
    console.log(s1) // Set(1) {1}
```

## 删除

使用 delete() 方法，即可在 Set 里面删除数据

```
    const s1 = new Set([1, 2, 3])
    console.log(s1) // Set(3) {1, 2, 3}
    s1.delete(2)
    console.log(s1) // Set(2) {1, 3}
```

## 清空

使用 delete() 方法，即可清空 Set 的所有数据

```
    const s1 = new Set([1, 2, 3])
    console.log(s1) // Set(3) {1, 2, 3}
    s1.clear()
    console.log(s1) // Set(0) {}
```

## 查询

### 查询是否包含某个值

使用 has() 方法，可以判断 Set 里面是否有某个数据

```
    const s1 = new Set([1, 2, 3])
    console.log(s1) // Set(3) {1, 2, 3}
    console.log(s1.has(2)) // true
    console.log(s1.has(4)) // false
```

### 查询拥有多少条数据

使用 size() 方法，可以获取 Set 拥有多少条数据

```
    const s1 = new Set([1, 2, 3])
    console.log(s1) // Set(3) {1, 2, 3}
    console.log(s1.size) // 3
```

## 遍历

```
    const s1 = new Set([1, 2, 3])

    s1.forEach(item => {
        console.log(item)
    })

    for(let item of s1) {
        console.log(item)
    }

    for(let item of s1.keys()) {
        console.log(item)
    }

    for(let item of s1.values()) {
        console.log(item)
    }

    for(let item of s1.entries()) {
        console.log(item[0], item[1])
    }
```

## 转换为数组

Set 行为和数组类似，所以 Set 可以轻易的转换成数组

```
    const s1 = new Set([1, 2, 3])
    console.log([...s1]) // [1, 2, 3]
    console.log(Array.from(s1)) // [1, 2, 3]
```

# WeakSet

WeakSet 只能保存对象  
WeakSet 的方法和 Set 类似

1. add
2. delete
3. has

WeakSet 不能遍历  
WeakSet 是一种弱引用，这种引用是不记录垃圾回收机制的
