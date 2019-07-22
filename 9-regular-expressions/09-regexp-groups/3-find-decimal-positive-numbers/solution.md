
<<<<<<< HEAD
`pattern:\d+` 可以匹配一个整数。

`pattern:\.\d+` 可以匹配小数部分。

因为小数部分不一定存在，所以我们将其放入捕获括号内，搭配量词 `pattern:'?'`。

最终我们得到这样一个正则表达式：`pattern:\d+(\.\d+)?`。

```js run
let reg = /\d+(\.\d+)?/g;

let str = "1.5 0 12. 123.4.";

alert( str.match(re) );   // 1.5, 0, 12, 123.4
=======
An non-negative integer number is `pattern:\d+`. A zero `0` can't be the first digit,  but we should allow it in further digits.

So that gives us `pattern:[1-9]\d*`.

A decimal part is: `pattern:\.\d+`.

Because the decimal part is optional, let's put it in parentheses with the quantifier `pattern:?`.

Finally we have the regexp: `pattern:[1-9]\d*(\.\d+)?`:

```js run
let reg = /[1-9]\d*(\.\d+)?/g;

let str = "1.5 0 -5 12. 123.4.";

alert( str.match(reg) );   // 1.5, 0, 12, 123.4
>>>>>>> 4a8d8987dfc3256045e6b4a3bd8810ad3b25d1b3
```
