# Iterator 迭代器

[Iterator](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Iterator)

## 可迭代协议

可迭代协议允许 JavaScript 对象定义或定制它们的迭代行为，例如，在一个 for..of 结构中，哪些值可以被遍历到。一些内置类型同时是内置可迭代对象，并且有默认的迭代行为，比如 Array 或者 Map，而其他内置类型则不是（比如 Object)）。  

要成为可迭代对象， 一个对象必须实现 @@iterator 方法。这意味着对象（或者它原型链上的某个对象）必须有一个键为 @@iterator 的属性，可通过常量 Symbol.iterator 访问该属性

当一个对象需要被迭代的时候（比如被置入一个 for...of 循环时），首先，会不带参数调用它的 @@iterator 方法，然后使用此方法返回的迭代器获得要迭代的值。  

值得注意的是调用此零个参数函数时，它将作为对可迭代对象的方法进行调用。 因此，在函数内部，this关键字可用于访问可迭代对象的属性，以决定在迭代过程中提供什么。  

此函数可以是普通函数，也可以是生成器函数，以便在调用时返回迭代器对象。 在此生成器函数的内部，可以使用yield提供每个条目。  

## 迭代器协议

迭代器协议定义了产生一系列值（无论是有限个还是无限个）的标准方式。当值为有限个时，所有的值都被迭代完毕后，则会返回一个默认返回值。  

只有实现了一个拥有以下语义（semantic）的 next() 方法，一个对象才能成为迭代器：  
一个无参数函数，返回一个应当拥有以下两个属性的对象：

done（boolean）  
如果迭代器可以产生序列中的下一个值，则为 false。（这等价于没有指定  done 这个属性。）  

如果迭代器已将序列迭代完毕，则为 true。这种情况下，value 是可选的，如果它依然存在，即为迭代结束之后的默认返回值。

value  
迭代器返回的任何 JavaScript 值。done 为 true 时可省略。  

next() 方法必须返回一个对象，该对象应当有两个属性： done 和 value，如果返回了一个非对象值（比如 false 或 undefined），则会抛出一个 TypeError 异常（"iterator.next() returned a non-object value"）。  

## 示例

可以配合 Generator 使用

```
    const obj = {
        name: 'Tiga',
        age: 24
    }

    obj[Symbol.iterator] = function() {
        const keys = Reflect.ownKeys(this)
        return {
            next() {
                return {
                    done: !keys.length,
                    value: this[keys.shift()]
                }
            }
        }
    }
```