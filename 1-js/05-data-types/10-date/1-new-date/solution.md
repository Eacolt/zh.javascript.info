<<<<<<< HEAD
`new Date` 构造函数默认使用当地时区。所以唯一需要牢记的是月份从 0 开始计数。
=======
The `new Date` constructor uses the local time zone. So the only important thing to remember is that months start from zero.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

所以二月对应的数值是 1。

```js run
let d = new Date(2012, 1, 20, 3, 12);
alert( d );
```
