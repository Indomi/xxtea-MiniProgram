# XXTEA 加密算法的 mini-program 实现

<a href="https://github.com/xxtea/">
    <img src="https://avatars1.githubusercontent.com/u/6683159?v=3&s=86" alt="XXTEA logo" title="XXTEA" align="right" />
</a>

[![License](https://img.shields.io/github/license/xxtea/xxtea-html5.svg)](http://opensource.org/licenses/MIT)

[![Sauce Test Status](https://saucelabs.com/browser-matrix/xxtea-html5.svg)](https://saucelabs.com/u/xxtea-html5)

## 简介

XXTEA 是一个快速安全的加密算法。本项目是 XXTEA 加密算法的 miniprogram 实现。

它不同于原始的 XXTEA 加密算法。它是针对 Uint8Array 类型数据进行加密的，而不是针对 uint32 数组。同样，密钥也是 Uint8Array 类型。如果你想加密字符串，你可以使用 xxtea.toBytes(str) 来将字符串转换为 Uint8Array。当你解密 Uint8Array 时，你可以使用 xxtea.toString(bytes) 来将结果转换为字符串。字符串与 Uint8Array 之间的转换，是采用 UTF8 编码的。

## 使用

```javascript
const xxtea = require('xxtea.js');

var str = "Hello World! 你好，中国！";
var key = "1234567890";
var encrypt_data = xxtea.encrypt(xxtea.toBytes(str), xxtea.toBytes(key));
console.log((btoa(String.fromCharCode.apply(String, encrypt_data))));
var decrypt_data = xxtea.toString(xxtea.decrypt(encrypt_data, xxtea.toBytes(key)));
console.assert(str === decrypt_data);
```

## 更新日志

1.1.0 更新

* 修正了表情符编码解码的问题。
* 改进了长字符串的加密解密。
* 增加了 `encryptToString` 和 `decryptToString` 方法，例如：

```javascript
const xxtea = require('xxtea.js');

var str = "Hello World! 你好，中国🇨🇳！";
var key = "1234567890";
var encrypt_data = xxtea.encryptToString(str, key);
console.log(encrypt_data);
var decrypt_data = xxtea.decryptToString(encrypt_data, key);
console.assert(str === decrypt_data);
```
