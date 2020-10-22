# Reflect 反射

具体还是看看 MDN 把，这玩意很强大啊！  
[Reflect](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect)

与大多数全局对象不同Reflect并非一个构造函数，所以不能通过new运算符对其进行调用，或者将Reflect对象作为一个函数来调用。Reflect的所有属性和方法都是静态的（就像Math对象）。

Reflect 对象提供了以下静态方法，这些方法与proxy handler methods的命名相同.

其中的一些方法与 Object相同, 尽管二者之间存在 某些细微上的差别 .

1. 将 Object 属于语言内部的方法放到 Reflect 上
2. 修改某些 Object 方法的返回结果， 让其变得更合理
3. 让 Object 操作变成函数行为
4. Reflect 对象的方法与 Proxy 对象的方法一一对应