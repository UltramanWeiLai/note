# BigInt 

2020 ES11 推出的基础数据类型  

## 声明

```
    const bigInt = 9007199254740993n
    console.log(bigInt) // 9007199254740993n
    console.log(typeof bigInt) // bigint
    console.log(1n == 1) // true | 值相等
    console.log(1n === 1) // false | int !== bigint

    const bigInt2 = BigInt(9007199254740993n)
    console.log(bigInt2) // 9007199254740993n

    const bigInt3 = bigInt + bigInt2
    console.log(bigInt3) // 18014398509481986n
    console.log(bigInt3.toString()) // 18014398509481986
```