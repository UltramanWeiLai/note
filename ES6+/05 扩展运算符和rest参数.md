# 扩展运算符 ...

## 展开

把数组或者类数组展开成逗号隔开的值

```
    {
        const fn = function(a, b, c) {
            return a + b + c
        }

        let arr = [1, 2, 3]

        fn(...arr) // ...arr 把 arr 展开成了 1, 2, 3 等同于：fn(1, 2, 3)
    }

    // ------------------------------

    {
        let arr1 = [1, 2, 3]
        let arr2 = [4, 5, 6]

        arr1.push(...arr2) // 等同于： arr.push(4, 5, 6)
    }

    // ------------------------------

    {
        const str = 'Tiga'
        const arr = [...str] // 等同于： arr = ['T', 'i', 'g', 'a']
    }

    // ------------------------------

    {
        const obj1 = {
            name: 'Tiga',
            age: 24
        }

        console.log({...obj1}) // { name: 'Tiga', age: 24 }
    }

    
```

## rest 

把逗号隔开的值组合成一个数组

```
    {
        const fn = function (...args) {
            // arguments
            return args
        }

        fn(1) // [1]
        fn(1, 2) // [1, 2]
        fn(1, 2, 3) // [1, 2, 3]
    }

    {
        const fn = function (a, ...args) {
            // arguments
            return args
        }

        fn(1) // []
        fn(1, 2) // [2]
        fn(1, 2, 3) // [2, 3]
    }

    {
        const obj1 = {
            name: 'Tiga'
        }

        const obj2 = {
            age: 24
        }

        // 浅克隆
        const obj3 = {
            ...obj1,
            ...obj2,
            ooo: '111'
        }

        const { name, ...rest } = obj3

        // name: 'Tiga' rest: { age: 24, ooo: '111' }
    }

```