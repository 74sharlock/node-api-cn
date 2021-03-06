
<!--introduced_in=v0.1.90-->

> 稳定性: 2 - 稳定的

在引入 [`TypedArray`] 之前，JavaScript 没有读取或操作二进制数据流的机制。
`Buffer` 类用于在 TCP 流或文件系统操作等场景中处理字节流。

现在有了 `TypedArray`，`Buffer` 类以一种更优化、更适合 Node.js 的方式实现了 [`Uint8Array`]。

`Buffer` 类的实例类似于整数数组，但 `Buffer` 的大小是固定的、且在 V8 堆外分配物理内存。
`Buffer` 的大小在创建时确定，且无法改变。

`Buffer` 类是一个全局变量，使用时无需 `require('buffer').Buffer`。

```js
// 创建一个长度为 10、且用 0 填充的 Buffer。
const buf1 = Buffer.alloc(10);

// 创建一个长度为 10、且用 0x1 填充的 Buffer。 
const buf2 = Buffer.alloc(10, 1);

// 创建一个长度为 10、且未初始化的 Buffer。
// 这个方法比调用 Buffer.alloc() 更快，但返回的 Buffer 实例可能包含旧数据，因此需要使用 fill() 或 write() 重写。
const buf3 = Buffer.allocUnsafe(10);

// 创建一个包含 [0x1, 0x2, 0x3] 的 Buffer。
const buf4 = Buffer.from([1, 2, 3]);

// 创建一个包含 UTF-8 字节 [0x74, 0xc3, 0xa9, 0x73, 0x74] 的 Buffer。
const buf5 = Buffer.from('tést');

// 创建一个包含 Latin-1 字节 [0x74, 0xe9, 0x73, 0x74] 的 Buffer。
const buf6 = Buffer.from('tést', 'latin1');
```

