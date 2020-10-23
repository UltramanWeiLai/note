# Generator

生成器对象是由一个 generator function 返回的,并且它符合可迭代协议和迭代器协议。

## 使用

```
    function* gen() { 
        yield 1;
        yield 2;
        yield 3;
    }
```

## 方法

### Generator.prototype.next()

next() 方法返回一个包含属性 done 和 value 的对象。  
该方法也可以通过接受一个参数用以向生成器传值，该值表示上一次的 yield 的返回值。

```
    function * foo() {
        for(let i = 0; i < 3; i++) {
            yield i
        }
    }

    const f = foo()
    console.log(f) // Generator { }
    console.log(f.next()) // { value: 0, done: false }
    console.log(f.next()) // { value: 1, done: false }
    console.log(f.next()) // { value: 2, done: false }
    console.log(f.next()) // { value: undefined, done: true }

    function* gen(x) {
        const y = 2 * (yield(x + 1))
        const z = yield(y / 3)
        return x + y + z
    }

    const g1 = gen(5)
    console.log(g1) // Generator { }
    console.log(g1.next()) // { value: 6, done: false }
    // 由于 next 没有传值，所以 y = 2 * undefined
    console.log(g1.next()) // { value: NaN, done: false } 
    // 由于 next 没有传值，所以 z = undefined
    console.log(g1.next()) // { value: NaN, done: false }

    const g2 = gen(2)
    console.log(g1) // Generator { }
    console.log(g1.next()) // { value: 6, done: false }
    // next 传值为12 y = 2 * 12 | 24 / 3 | 8
    console.log(g1.next(12)) // { value: 8, done: false } 
    // next 传值为13 z = 13 | 5 + 24 + 13 | 42
    console.log(g1.next(13)) // { value: 42, done: false } 
```

### Generator.prototype.return()

return() 方法返回给定的值并结束生成器。

```
    function * foo() {
        for(let i = 0; i < 3; i++) {
            yield i
        }
    }

    const f = foo()
    console.log(f) // Generator { }
    console.log(f.next()) // { value: 0, done: false }
    console.log(f.return('foo')) // { value: 'foo', done: true }
    console.log(f.next()) // { value: undefined, done: true }
    console.log(f.return()) // { value: undefined, done: true }
    console.log(f.return('foo1')) // { value: 'foo1', done: true }
```
    

### Generator.prototype.throw()

throw() 方法用来向生成器抛出异常，并恢复生成器的执行，返回带有 done 及 value 两个属性的对象。

```
    function* gen() {
        while(true) {
            try {
                yield 42;
            } catch(e) {
                console.log("Error caught!");
            }
        }
    }

    var g = gen();
    g.next(); // { value: 42, done: false }
    g.throw(new Error("Something went wrong")); 
```