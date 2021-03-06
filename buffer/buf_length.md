<!-- YAML
added: v0.1.90
-->

* {integer}

返回内存中分配给 `buf` 的字节数。
不一定反映 `buf` 中可用数据的字节量。

```js
// 创建一个 `Buffer`，并写入一个 ASCII 字符串。

const buf = Buffer.alloc(1234);

console.log(buf.length);
// 输出: 1234

buf.write('http://nodejs.cn/', 0, 'ascii');

console.log(buf.length);
// 输出: 1234
```

虽然 `length` 属性不是不可变的，但改变 `length` 的值可能会造成不确定的结果。
如果想改变一个 `Buffer` 的长度，应该使用 [`buf.slice()`] 创建一个新的 `Buffer`。

```js
let buf = Buffer.allocUnsafe(10);

buf.write('abcdefghj', 0, 'ascii');

console.log(buf.length);
// 输出: 10

buf = buf.slice(0, 5);

console.log(buf.length);
// 输出: 5
```

