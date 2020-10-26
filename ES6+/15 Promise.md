# Promise

Promise 对象用于表示一个异步操作的最终完成 (或失败)及其结果值  

一个 Promise 必然处于以下几种状态之一：
1. 待定（pending）: 初始状态，既没有被兑现，也没有被拒绝。
2. 已兑现（fulfilled）: 意味着操作成功完成。
3. 已拒绝（rejected）: 意味着操作失败。

## 成功状态 Promise.prototype.then()

```
    new Promise(resolve => {
        //...
        resolve('成功')
    }) // 成功状态
    .then() // 接受成功状态后返回成功状态
```

## 失败状态 Promise.prototype.catch()

```
    new Promise((resolve, reject) => {
        //...
        reject('失败')
    }) // 失败状态
    .catch() // 接受失败状态后返回成功状态
```

## 必定执行 Promise.prototype.finally()

```
    new Promise((resolve, reject) => {
        //...
        reject('失败') || resolve('成功')
    }) 
    .finally() // 不管成功还是失败都会执行
```

## Promise.all(iterable)

等待 iterable 数组中所有的代码执行完成后，返回一个返回值的数组  
当 iterable 数组中的执行代码有一个返回失败的时候，就只返回该信息

这个方法返回一个新的promise对象  
该promise对象在iterable参数对象里所有的promise对象都成功的时候才会触发成功  
一旦有任何一个iterable里面的promise对象失败则立即触发该promise对象的失败  
这个新的promise对象在触发成功状态以后，会把一个包含iterable里所有promise返回值的数组作为成功回调的返回值，顺序跟iterable的顺序保持一致  
如果这个新的promise对象触发了失败状态，它会把iterable里第一个触发失败的promise对象的错误信息作为它的失败错误信息  
Promise.all方法常被用于处理多个promise对象的状态集合

## Promise.allSettled(iterable)

正常返回所有 iterable 的内容，不会因为某个状态是失败而只返回失败

等到所有promises都已敲定（settled）（每个promise都已兑现（fulfilled）或已拒绝（rejected））。  
返回一个promise，该promise在所有promise完成后完成。并带有一个对象数组，每个对象对应每个promise的结果。

## Promise.any(iterable)

接收一个Promise对象的集合，当其中的一个 promise 成功，就返回那个成功的promise的值。

## Promise.race(iterable)

当iterable参数里的任意一个子promise被成功或失败后，父promise马上也会用子promise的成功返回值或失败详情作为参数调用父promise绑定的相应句柄，并返回该promise对象。

## Promise.reject(reason)

返回一个状态为失败的Promise对象，并将给定的失败信息传递给对应的处理方法

## Promise.resolve(value)

返回一个状态为成功的 Promise 对象

返回一个状态由给定value决定的Promise对象。如果该值是thenable(即，带有then方法的对象)，返回的Promise对象的最终状态由then方法执行决定；否则的话(该value为空，基本类型或者不带then方法的对象),返回的Promise对象状态为fulfilled，并且将该value传递给对应的then方法。通常而言，如果您不知道一个值是否是Promise对象，使用Promise.resolve(value) 来返回一个Promise对象,这样就能将该value以Promise对象形式使用。

