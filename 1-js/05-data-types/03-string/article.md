# 字符串

在 JavaScript 中，文本数据被作为字符串存储，字符没有单独的类型。

字符串的内部格式总是 [UTF-16](https://en.wikipedia.org/wiki/UTF-16)，它不会绑定到页面编码中。

## Quotes

让我们回忆一下这些引语。

字符串可以包含在单引号、双引号或反引号中：

```js
let single = 'single-quoted';
let double = "double-quoted";

let backticks = `backticks`;
```

<<<<<<< HEAD
单引号和双引号本质上是一样的。但是，反引号允许我们将任何表达式嵌入到字符串中，包括函数调用：
=======
Single and double quotes are essentially the same. Backticks, however, allow us to embed any expression into the string, by wrapping it in `${…}`:
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

```js run
function sum(a, b) {
  return a + b;
}

alert(`1 + 2 = ${sum(1, 2)}.`); // 1 + 2 = 3.
```

使用反引号的另一个优点是它们允许字符串跨行：

```js run
let guestList = `Guests:
 * John
 * Pete
 * Mary
`;

alert(guestList); // 客人清单，多行
```

<<<<<<< HEAD
如果我们尝试以相同的方式使用单引号或双引号，则会出错：
=======
Looks natural, right? But single or double quotes do not work this way.

If we use them and try to use multiple lines, there'll be an error:

>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7
```js run
let guestList = "Guests: // Error: Unexpected token ILLEGAL
  * John";
```

当不考虑多行字符串的需要时，单引号和双引号来自语言创建的古时代。反引号出现较晚，因此更通用。

反引号还允许我们在第一个反引号之前指定一个“模版函数”。语法是：<code>func&#96;string&#96;</code>。函数 `func` 被自动调用，接收字符串和嵌入式表达式，并处理它们。你可以在 [docs](mdn:/JavaScript/Reference/Template_literals#Tagged_template_literals) 中阅读更多关于它们的信息。这叫做 "tagged templates"。此功能可以更轻松地将字符串包装到自定义模版或其他函数中，但这很少使用。

<<<<<<< HEAD

## 特殊字符

通过使用换行符 `\n` 来创建带有单引号的多行字符串，它表示中断：
=======
## Special characters

It is still possible to create multiline strings with single and double quotes by using a so-called "newline character", written as `\n`, which denotes a line break:
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

```js run
let guestList = "Guests:\n * John\n * Pete\n * Mary";

alert(guestList); // a multiline list of guests
```

<<<<<<< HEAD
例如，这两行描述相同：
=======
For example, these two lines are equal, just written differently:
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

```js run
let str1 = "Hello\nWorld"; // two lines using a "newline symbol"

// two lines using a normal newline and backticks
let str2 = `Hello
World`;

alert(str1 == str2); // true
```

<<<<<<< HEAD
还有其他不常见的“特殊字符”，列表如下：
=======
There are other, less common "special" characters.

Here's the full list:
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

| 字符 | 描述 |
|-----------|-------------|
|`\n`|New line|
|`\r`|Carriage return: not used alone. Windows text files use a combination of two characters `\r\n` to represent a line break. |
|`\'`, `\"`|Quotes|
|`\\`|Backslash|
|`\t`|Tab|
<<<<<<< HEAD
|`\uNNNN`|16 进制的 `NNNN` 的unicode 符号，例如 `\u00A9`—— 是版权符号的 unicode `©`。它必须是 4 个16 进制数字。 |
|`\u{NNNNNNNN}`|一些罕见字符使用两个 unicode 符号进行编码，最多占用 4 个字节。这个长的 unicode 需要它周围的括号。|
=======
|`\b`, `\f`, `\v`| Backspace, Form Feed, Vertical Tab -- kept for compatibility, not used nowadays. |
|`\xXX`|Unicode character with the given hexadimal unicode `XX`, e.g. `'\x7A'` is the same as `'z'`.|
|`\uXXXX`|A unicode symbol with the hex code `XXXX` in UTF-16 encoding, for instance `\u00A9` -- is a unicode for the copyright symbol `©`. It must be exactly 4 hex digits. |
|`\u{X…XXXXXX}` (1 to 6 hex characters)|A unicode symbol with the given UTF-32 encoding. Some rare characters are encoded with two unicode symbols, taking 4 bytes. This way we can insert long codes. |
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

unicode 示例：

```js run
alert( "\u00A9" ); // ©
alert( "\u{20331}" ); // 佫, a rare Chinese hieroglyph (long unicode)
alert( "\u{1F60D}" ); // 😍, a smiling face symbol (another long unicode)
```

所有的特殊字符都以反斜杠字符 `\` 开始。它也被称为“转义字符”。

<<<<<<< HEAD
如果我们想要在字符串中插入一个引号，我们也会使用它。
=======
We might also use it if we wanted to insert a quote into the string.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

例如：

```js run
alert( 'I*!*\'*/!*m the Walrus!' ); // *!*I'm*/!* the Walrus!
```

正如你所看到的，我们必须用反斜杠 `\'` 来预设值内部引号，否则就表示字符串结束。

<<<<<<< HEAD
当然，这只不过是指与上文相同的引文。因此，作为更优雅的解决方案，我们可以改用双引号或反引号。
=======
Of course, only to the quotes that are the same as the enclosing ones need to be escaped. So, as a more elegant solution, we could switch to double quotes or backticks instead:
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

```js run
alert( `I'm the Walrus!` ); // I'm the Walrus!
```

注意反斜杠 `\` 在 JavaScript 中用于正确读取字符串，然后消失。内存中的字符串没有 `\`。从上述示例中的 `alert` 可以清楚地看到 。

但是如果我们需要在字符串中显示一个实际的反斜杠 `\` 应该怎么做？

我们可以这样做，只需要将其书写两次 `\\`：

```js run
alert( `The backslash: \\` ); // The backslash: \
```

## 字符串长度

<<<<<<< HEAD

`length` 属性有字符串长度：
=======
The `length` property has the string length:
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

```js run
alert( `My\n`.length ); // 3
```

注意 `\n` 是一个单独的“特殊”字符，所以长度确实是 `3`

```warn header="`length` is a property"
掌握其他语言的人，有时会错误地调用 `str.length()` 而不是 `str.length`。这是行不通的。

<<<<<<< HEAD
请注意 `str.length` 是一个数字属性，而不是函数。之后不需要添加括号。
=======
Please note that `str.length` is a numeric property, not a function. There is no need to add parenthesis after it.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7
```

## 访问字符。

在 `pos` 位置获取一个字符，可以使用方括号 `[pos]` 或者调用 [str.charAt(pos)](mdn:js/String/charAt) 方法。第一个字符从零位置开始：

```js run
let str = `Hello`;

// the first character
alert( str[0] ); // H
alert( str.charAt(0) ); // H

// the last character
alert( str[str.length - 1] ); // o
```

方括号是获取字符的一种现代化方法，而 `charAt` 是历史原因才存在的。

它们之间的唯一区别是，如果没有找到字符，`[]` 返回 `undefined`，而 `charAt` 返回一个空字符串：

```js run
let str = `Hello`;

alert( str[1000] ); // undefined
alert( str.charAt(1000) ); // '' (an empty string)
```

我们也可以使用 `for..of` 遍历字符：

```js run
for (let char of "Hello") {
  alert(char); // H,e,l,l,o (char becomes "H", then "e", then "l" etc)
}
```

## 字符串不可变

在 JavaScript 中，字符串不可更改。改变字符是不可能的。

我们证明一下为什么不可能：

```js run
let str = 'Hi';

str[0] = 'h'; // error
alert( str[0] ); // 无法运行
```

通常的解决方法是创建一个新的字符串，并将其分配给 `str` 而不是以前的字符串。

例如：

```js run
let str = 'Hi';

<<<<<<< HEAD
str = 'h' + str[1];  // 字符串替换
=======
str = 'h' + str[1]; // replace the string
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

alert( str ); // hi
```

下面的文章，我们将看到跟多的示例。

## 改变大小写

[toLowerCase()](mdn:js/String/toLowerCase) 和 [toUpperCase()](mdn:js/String/toUpperCase) 可以改变大小写：

```js run
alert( 'Interface'.toUpperCase() ); // INTERFACE
alert( 'Interface'.toLowerCase() ); // interface
```

或者我们想要一个小写字符：

```js
alert( 'Interface'[0].toLowerCase() ); // 'i'
```

## 查找子字符串

在字符串中查找子字符串有很多种方法。

### str.indexOf

第一个方法是 [str.indexOf(substr, pos)](mdn:js/String/indexOf)。

它从给定位置 `pos` 开始，在 `str` 中查找 `substr`，如果没有找到，则返回 `-1`，否则返回匹配成功的位置。

例如：

```js run
let str = 'Widget with id';

alert( str.indexOf('Widget') ); // 0，因为 'Widget' 一开始就被找到
alert( str.indexOf('widget') ); // -1，没有找到，检索是大小写敏感的

alert( str.indexOf("id") ); // 1，"id" 在位置 1 处（...idget 和 id）
```

可选的第二个参数允许我们从给定的起始位置开始检索

例如，`"id"` 第一次出现的位置是 `1`。查询下一个存在位置时，我们从 `2` 开始检索：

```js run
let str = 'Widget with id';

alert( str.indexOf('id', 2) ) // 12
```

<<<<<<< HEAD

如果我们对所有存在位置都感兴趣，可以在一个循环中使用 `indexOf`。每一次新的调用都发生在上一匹配位置之后：
=======
If we're interested in all occurrences, we can run `indexOf` in a loop. Every new call is made with the position after the previous match:
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

```js run
let str = 'As sly as a fox, as strong as an ox';

let target = 'as'; // 让我们查看一下

let pos = 0;
while (true) {
  let foundPos = str.indexOf(target, pos);
  if (foundPos == -1) break;

  alert( `Found at ${foundPos}` );
  pos = foundPos + 1; // 继续从下一个位置查找
}
```

相同的算法可以简写：

```js run
let str = "As sly as a fox, as strong as an ox";
let target = "as";

*!*
let pos = -1;
while ((pos = str.indexOf(target, pos + 1)) != -1) {
  alert( pos );
}
*/!*
```

<<<<<<< HEAD
```smart header="`str.lastIndexOf(subStr, pos)`"
还有一个类似的方法 [str.lastIndexOf(subStr, pos)](mdn:js/String/lastIndexOf)，他从字符串的末尾开始搜索。
=======
```smart header="`str.lastIndexOf(substr, position)`"
There is also a similar method [str.lastIndexOf(substr, position)](mdn:js/String/lastIndexOf) that searches from the end of a string to its beginning.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

它会以相反的顺序列出事件。
```

在 `if` 测试中 `indexOf` 有一点不方便。我们不可以把它放在这样的 `if` 中：

```js run
let str = "Widget with id";

if (str.indexOf("Widget")) {
    alert("We found it"); // doesn't work!
}
```

上述示例中的 `alert` 不会显示，因为 `str.indexOf("Widget")` 返回 `0`（意思是它在起始位置查找匹配）。是的，但是  `if` 认为 `0` 应该是 `false`。

因此我们实际上是从 `-1` 开始的，就像这样：

```js run
let str = "Widget with id";

*!*
if (str.indexOf("Widget") != -1) {
*/!*
    alert("We found it"); // 现在运行了！
}
```

<<<<<<< HEAD
````smart header="The bitwise NOT trick"
这里使用的一个老技巧是 [bitwise NOT](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators#Bitwise_NOT) `~` 运算符。它将该数字转换为 32-bit 整数（如果存在，则删除小数部分），然后反转其二进制表示中的所有位。
=======
#### The bitwise NOT trick

One of the old tricks used here is the [bitwise NOT](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators#Bitwise_NOT) `~` operator. It converts the number to a 32-bit integer (removes the decimal part if exists) and then reverses all bits in its binary representation.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

对于 32-bit 整数，调用 `~n` 的意思与 `-(n+1)` 完全一样（由于 IEEE-754 格式）。

例如：

```js run
alert( ~2 ); // -3, the same as -(2+1)
alert( ~1 ); // -2, the same as -(1+1)
alert( ~0 ); // -1, the same as -(0+1)
*!*
alert( ~-1 ); // 0, the same as -(-1+1)
*/!*
```

<<<<<<< HEAD
正如我们看到这样，只有当 `n == -1` 时，`~n` 才为零。

因此，测试 `if ( ~str.indexOf("...") )` 真是 `indexOf` 的结果不是 `-1`。换句话说，当有匹配时。
=======
As we can see, `~n` is zero only if `n == -1` (that's for any 32-bit signed integer `n`).

So, the test `if ( ~str.indexOf("...") )` is truthy only if the result of `indexOf` is not `-1`. In other words, when there is a match.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

人们用它来简写 `indexOf` 检查：

```js run
let str = "Widget";

if (~str.indexOf("Widget")) {
  alert( 'Found it!' ); // works
}
```

通常不建议以非显而易见的方式使用语言特性，但这种特殊技巧在旧代码中仍被广泛使用，所以我们应该理解它。

<<<<<<< HEAD
只要记住：`if (~str.indexOf(...))` 读作 "if found"。
````
=======
Just remember: `if (~str.indexOf(...))` reads as "if found".

Technically speaking, numbers are truncated to 32 bits by `~` operator, so there exist other big numbers that give `0`, the smallest is `~4294967295=0`. That makes such check is correct only if a string is not that long.

Right now we can see this trick only in the old code, as modern JavaScript provides `.includes` method (see below).
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

### includes, startsWith, endsWith

更现代的方法 [str.includes(substr, pos)](mdn:js/String/includes) 取决于 `str` 是否包含 `substr` 来返回 `true/false`。

如果我们需要测试匹配，这是正确的选择，但不需要它的位置：

```js run
alert( "Widget with id".includes("Widget") ); // true

alert( "Hello".includes("Bye") ); // false
```

`str.includes` 的第二个可选参数从以下位置开始搜索位置：

```js run
alert( "Midget".includes("id") ); // true
alert( "Midget".includes("id", 3) ); // false, 位置 3 没有 "id"
```

方法 [str.startsWith](mdn:js/String/startsWith) 和 [str.endsWith](mdn:js/String/endsWith) 完全按照它们所说的执行：

```js run
<<<<<<< HEAD
alert( "Widget".startsWith("Wid") ); // true, "Widget" 以 "Wid" 开始
alert( "Widget".endsWith("get") );   // true, "Widget" 以 "get" 结束
=======
alert( "Widget".startsWith("Wid") ); // true, "Widget" starts with "Wid"
alert( "Widget".endsWith("get") ); // true, "Widget" ends with "get"
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7
```

## 获取子字符串

JavaScript 中有三种获取字符串的方法：`substring`、`substr` 和 `slice`。

`str.slice(start [, end])`
: 返回从 `start` 到（但不包括）`end` 的字符串部分。

    例如：

    ```js run
    let str = "stringify";
    alert( str.slice(0, 5) ); // 'strin', 从 0 到 5 的子字符串（不包括 5）
    alert( str.slice(0, 1) ); // 's', 从 0 到 1，但不包括 1，所以只有在 0 的字符
    ```

    如果没有第二个参数，`slice` 运行到字符串末尾：

    ```js run
    let str = "st*!*ringify*/!*";
    alert( str.slice(2) ); // 从第二个位置直到结束
    ```

    `start/end` 也有可能是负值。它们的意思是位置从字符串结尾计算：

    ```js run
    let str = "strin*!*gif*/!*y";

    // 从右边的第四个位置开始，在右边的第一个位置结束
    alert( str.slice(-4, -1) ); // */!
    ```

`str.substring(start [, end])`
: 返回 `start` 和 `end` **之间**的字符串部分。

    这与 `slice` 几乎相同，但它允许 `start`大于 `end`。

    例如：

    ```js run
    let str = "st*!*ring*/!*ify";

    // 这些对于子串是相同的
    alert( str.substring(2, 6) ); // "ring"
    alert( str.substring(6, 2) ); // "ring"

    // ...但除了 slice：
    alert( str.slice(2, 6) ); // "ring" (the same)
    alert( str.slice(6, 2) ); // "" (an empty string)

    ```

    否定参数（不像 slice）不支持，它们被视为 `0`。

`str.substr(start [, length])`
:  从 `start` 开始返回给定 `length` 的字符串部分。

    与以前的方法相比，这个允许我们指定 `length` 而不是结束位置：

    ```js run
    let str = "st*!*ring*/!*ify";
    alert( str.substr(2, 4) ); // 环，从第二位获得 4 个字符
    ```

    第一个参数可能是负数，从结尾算起：

    ```js run
    let str = "strin*!*gi*/!*fy";
    alert( str.substr(-4, 2) ); // gi，从第 4 位获得 2 个字符
    ```

我们回顾一下这些方法，以免混淆：

| method | selects... | negatives |
|--------|-----------|-----------|
| `slice(start, end)` | from `start` to `end` (not including `end`) | allows negatives |
| `substring(start, end)` | between `start` and `end` | negative values mean `0` |
| `substr(start, length)` | from `start` get `length` characters | allows negative `start` |

```smart header="Which one to choose?"
他们可以完成这项工作，形式上，`substr` 有一个小缺点：它不是在 JavaScript 核心规范中描述的，而是在附录 B 中，它涵盖了主要由于历史原因而存在的浏览器特性。因此，非浏览器环境可能无法支持它。但实际上它在任何地方都有效。

<<<<<<< HEAD
作者发现自己几乎一直在使用 `slice`。
=======
Of the other two variants, `slice` is a little bit more flexible, it allows negative arguments and shorter to write. So, it's enough to remember solely `slice` of these three methods.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7
```

## 比较字符串

正如我们从 <info:comparison> 一章中了解到的，字符串按字母顺序逐字比较。

不过，也有一些奇怪的地方。

1. 小写字母总是大于大写字母：

    ```js run
    alert( 'a' > 'Z' ); // true
    ```

2. 带有指示性标记的字母“不正常”：

    ```js run
    alert( 'Österreich' > 'Zealand' ); // true
    ```

    如果我们对这些国名进行排序，可能会导致奇怪的结果。通常，人们会期望 `Zealand` 在名单中的 `Österreich` 之后出现。

为了明白发生了什么，我们回顾一下在 JavaScript 中字符串的内部表示。

所有的字符串都使用 [UTF-16](https://en.wikipedia.org/wiki/UTF-16) 编码。即：每个字符都有相应的数字代码。有特殊的方法可以获取代码的字符并返回。

`str.codePointAt(pos)`
: 返回在 `pos` 位置的字符代码 :

    ```js run
    // 不同的字母有不同的代码
    alert( "z".codePointAt(0) ); // 122
    alert( "Z".codePointAt(0) ); // 90
    ```

`String.fromCodePoint(code)`
: 通过数字 `code` 创建字符

    ```js run
    alert( String.fromCodePoint(90) ); // Z
    ```

    我们还可以用

    ```js run
    // 90 is 5a in hexadecimal system
    alert( '\u005a' ); // Z
    ```

现在我们看一下代码 `65..220` 的字符（拉丁字母和一些额外的字符），方法是创建一个字符串：

```js run
let str = '';

for (let i = 65; i <= 220; i++) {
  str += String.fromCodePoint(i);
}
alert( str );
// ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_`abcdefghijklmnopqrstuvwxyz{|}~
// ¡¢£¤¥¦§¨©ª«¬­®¯°±²³´µ¶·¸¹º»¼½¾¿ÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖ×ØÙÚÛÜ
```

看到？大写字符先走，然后是一些特殊字符，然后是小写字符。

现在很明显为什么 `a > Z`。

字符通过数字代码进行比较。越大的代码意味着字符越大。`a`（97）的代码大于 `Z`（90）。

- 所有小写字母都是大写字母，因为它们的代码更大。
- 一些想 `Ö` 的字母与主要字母表不同。这里的代码比从 `a` 到 `z` 的代码都要大。

<<<<<<< HEAD

### 正确的比较

执行字符串比较的“正确”算法比看起来更复杂，因为不同语言的字母都不相同。相同的字母可能位于不同的字母表中。
=======
### Correct comparisons

The "right" algorithm to do string comparisons is more complex than it may seem, because alphabets are different for different languages.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

因此浏览器需要知道要比较的语言。

幸运地是，所有现代浏览器（IE-10 都需要额外的库 [Intl.JS](https://github.com/andyearnshaw/Intl.js/)) 支持国际化标准 [ECMA 402](http://www.ecma-international.org/ecma-402/1.0/ECMA-402.pdf)。

它提供了一种特殊的方法来比较不同语言的字符串，遵循它们的规则。

<<<<<<< HEAD
调用 [str.localeCompare(str2)](mdn:js/String/localeCompare)：

- 根据语言规则，如果 `str` 大于 `str2` 返回 `1`。
- 如果if `str` 小于 `str2` 返回 `-1`。
- 如果相等，返回 `0`。
=======
The call [str.localeCompare(str2)](mdn:js/String/localeCompare) returns an integer indicating whether `str` comes before, after or is equivalent to `str2` according to the language rules:

- Returns a negative number if `str` is less than `str2`, i.e. `str` occurs before `str2`.
- Returns a positive number if `str` is greater than `str2`, i.e. `str` occurs after `str2`.
- Returns `0` if they are equivalent.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

例如：

```js run
alert( 'Österreich'.localeCompare('Zealand') ); // -1
```

<<<<<<< HEAD
这个方法实际上在[文档](mdn:js/String/localeCompare)中指定了两个额外的参数，它允许它指定语言（默认从环境中获取）并设置诸如区别大小之类的附加规则，或应该处理将 `"a"` 和 `"á"` 看作相等情况等。
=======
This method actually has two additional arguments specified in [the documentation](mdn:js/String/localeCompare), which allows it to specify the language (by default taken from the environment, letter order depends on the language) and setup additional rules like case sensitivity or should `"a"` and `"á"` be treated as the same etc.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

## 内部，Unicode

```warn header="Advanced knowledge"
<<<<<<< HEAD
这部分会深入字符串内部。如果你计划处理表情符号、罕见的象形文字字符或其他罕见符号，这些知识会对你有用。
=======
The section goes deeper into string internals. This knowledge will be useful for you if you plan to deal with emoji, rare mathematical or hieroglyphic characters or other rare symbols.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

如果你不打算支持它们，你可以跳过这一部分。
```

### 代理对

<<<<<<< HEAD
大部分 symbol 都有一个 2 字节的代码。大多数欧洲语言，数字甚至大多数象形文字中的字母都有 2 字节的表示形式。
=======
All frequently used characters have 2-byte codes. Letters in most european languages, numbers, and even most hieroglyphs, have a 2-byte representation.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

但 2 字节只允许 65536 个组合，这对于每个可能的符号都是不够的。所以稀有的符号被称为“代理对”的一对 2 字节符号编码。

这些符号的长度是 `2`：

```js run
alert( '𝒳'.length ); // 2, MATHEMATICAL SCRIPT CAPITAL X
alert( '😂'.length ); // 2, FACE WITH TEARS OF JOY
alert( '𩷶'.length ); // 2, a rare Chinese hieroglyph
```

注意，代理对在 JavaScript 被创建时并不存在，因此无法被语言正确代理。

我们实际上在上面的每个字符串中都有一个符号，但 `length` 显示长度为 `2`。

`String.fromCodePoint` 和 `str.codePointAt` 是几种处理代理对的少数方法。它们最近在出现在语言中。在它们之前，只有 [String.fromCharCode](mdn:js/String/fromCharCode) 和 [str.charCodeAt](mdn:js/String/charCodeAt)。这些方法实际上与 `fromCodePoint/codePointAt` 相同，但是不适用于代理对。

<<<<<<< HEAD
但是，例如，获取符号可能会非常麻烦，因为代理对被认为是两个字符：
=======
Getting a symbol can be tricky, because surrogate pairs are treated as two characters:
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

```js run
alert( '𝒳'[0] ); // 奇怪的符号...
alert( '𝒳'[1] ); // ...代理对的一块
```

请注意，代理对的各部分没有任何意义。因此，上述示例中的 alert 显示实际上并没有用。

技术角度来说，代理对也是可以通过它们的代码检测到：如果一个字符的代码间隔为 `0xd800..0xdbff`，那么它是代理对的第一部分。下一个字符（第二部分）必须在时间间隔 `0xdc00..0xdfff` 中。这些间隔仅有标准的代理对保留。

在上述示例中：

```js run
// charCodeAt is not surrogate-pair aware, so it gives codes for parts

alert( '𝒳'.charCodeAt(0).toString(16) ); // d835, 在 0xd800 和 0xdbff 之间
alert( '𝒳'.charCodeAt(1).toString(16) ); // dcb3, 在 0xdc00 和 0xdfff 之间
```

本章节后面的 <info:iterable> 中可以找到更多处理代理对的方法。也可能有特殊的库，这里没有什么足够好的建议。

### 指示标志与规范化

在许多语言中，有一些符号是由上面/下面有标记的基本字符组成的。

例如，字母 `a` 可以是基本字符：`àáâäãåā`。最常见的“复合”字符在 UTF-16 表中有自己的代码。但不是全部，因为可能的组合太多。

<<<<<<< HEAD
为了支持任意组合，UTF-16 允许我们使用多个 unicode 字符。基本字符和“装饰”它的一个或多个“标记”字符。
=======
To support arbitrary compositions, UTF-16 allows us to use several unicode characters: the base character followed by one or many "mark" characters that "decorate" it.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

例如，如果我们 `S` 后跟有特殊的 "dot above" 字符（代码 `\u0307`），则显示 Ṡ。

```js run
alert( 'S\u0307' ); // Ṡ
```

如果我们需要在字母上方（或下方）添加额外的标记 —— 没问题，只需要添加必要的标记字符即可。

例如，如果我们追加一个字符 "dot below"（代码 `\u0323`），那么我们将得到“S 点以上和以下的”：`Ṩ`。

例如：

```js run
alert( 'S\u0307\u0323' ); // Ṩ
```

这在提供良好灵活性的同时，也存在一个有趣的问题：两个视觉上看起来相同的字符，可以用不同的 unicode 组合表示。

例如：

```js run
alert( 'S\u0307\u0323' ); // Ṩ, S + dot above + dot below
alert( 'S\u0323\u0307' ); // Ṩ, S + dot below + dot above

alert( 'S\u0307\u0323' == 'S\u0323\u0307' ); // false, different characters (?!)
```

为了解决这个问题，有一个 “unicode 规范化”算法，它将每个字符串都转化成单个“通用”格式。

它由 [str.normalize()](mdn:js/String/normalize) 实现。

```js run
alert( "S\u0307\u0323".normalize() == "S\u0323\u0307".normalize() ); // true
```

我们遇到的有趣现象是实际上 `normalize()` 将一个由 3 个字符组成的序列合并为一个：`\u1e68`（S 有两个点）。

```js run
alert( "S\u0307\u0323".normalize().length ); // 1

alert( "S\u0307\u0323".normalize() == "\u1e68" ); // true
```

<<<<<<< HEAD
事实上，情况并非总是如此，因为符号 `Ṩ` “常用”，所以 UTF-16 创建者把它包含在主表中并给了它代码。
=======
In reality, this is not always the case. The reason being that the symbol `Ṩ` is "common enough", so UTF-16 creators included it in the main table and gave it the code.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

如果你想了解更多关于规范化规则和变体的信息 —— 它们在 Unicode 标准附录中有详细描述：[Unicode 规范化形式](http://www.unicode.org/reports/tr15/)，但对于大多数实际目的来说，本文的内容就已经足够了。

<<<<<<< HEAD

## 总结

- 有 3 种类型的引号，反引号允许字符串跨越多行并嵌入表达式。
- JavaScript 中的字符串使用 UTF-16 进行编码。
- 我们可以使用像 `\n` 这样的特殊字符或通过使用 `\u...` 来操作它们的 unicode 进行字符插入。 
- 获取字符时，使用 `[]`。
- 获取子字符串，使用 `slice` 或 `substring`。
- 字符串的大/小写转换，使用：`toLowerCase/toUpperCase`。
- 查找子字符串时，使用 `indexOf` 或 `includes/startsWith/endsWith` 进行简单检查。
- 根据语言比较字符串时使用 `localeCompare`，否则将按字符代码进行比较。
=======
## Summary

- There are 3 types of quotes. Backticks allow a string to span multiple lines and embed expressions `${…}`.
- Strings in JavaScript are encoded using UTF-16.
- We can use special characters like `\n` and insert letters by their unicode using `\u...`.
- To get a character, use: `[]`.
- To get a substring, use: `slice` or `substring`.
- To lowercase/uppercase a string, use: `toLowerCase/toUpperCase`.
- To look for a substring, use: `indexOf`, or `includes/startsWith/endsWith` for simple checks.
- To compare strings according to the language, use: `localeCompare`, otherwise they are compared by character codes.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7

字符串还有其他几种有用的方法：

<<<<<<< HEAD
- `str.trim()` —— 删除字符串前后的空格 ("trims")。
- `str.repeat(n)` —— 重复字符串 `n` 次。
- ...更多内容细节参见[手册](mdn:js/String)。

字符串还具有用正则表达式执行搜索/替换的方法。但这个话题值得拥有单独的一章，所以我们稍后再说。
=======
- `str.trim()` -- removes ("trims") spaces from the beginning and end of the string.
- `str.repeat(n)` -- repeats the string `n` times.
- ...and more to be found in the [manual](mdn:js/String).

Strings also have methods for doing search/replace with regular expressions. But that's big topic, so it's explained in a separate tutorial section <info:regular-expressions>.
>>>>>>> be342e50e3a3140014b508437afd940cd0439ab7
