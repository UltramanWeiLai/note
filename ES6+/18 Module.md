# Module

## CommonJS node.js

## AMD require.js

## CMD sea.js

## ES6

```
    {
        // a.js
        export const a1 = 5
        export const a2 = 10
        export const sum = (x, y) => x + y
        
        const obj = {
            name: 'es'
        }
        export { obj }
        export const _a3 = 15

        /* export {
            a, 
            b, 
            sum, 
            obj
        } */

        const a = 20
        export default a
    }

    {
        b.js
        import aaa, { a1, a2, sum, obj, _a3 as a3 } from './a.js'
        import * as mod from './a.js' // default & a1, a2 ,a3, ...

        console.log(a1) // 5
        console.log(a2) // 10
        console.log(sum(a1, a2)) // 15
        console.log(obj) // { name: 'es' }
        console.log(_a3) // error
        console.log(a3) // 15
        console.log(aaa) // 20
    }
```
