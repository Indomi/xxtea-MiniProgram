# XXTEA for mini-program

<a href="https://github.com/xxtea/">
    <img src="https://avatars1.githubusercontent.com/u/6683159?v=3&s=86" alt="XXTEA logo" title="XXTEA" align="right" />
</a>

[![License](https://img.shields.io/github/license/xxtea/xxtea-html5.svg)](http://opensource.org/licenses/MIT)

## Introduction

XXTEA is a fast and secure encryption algorithm. This is a XXTEA library for miniprogram.

It is different from the original XXTEA encryption algorithm. It encrypts and decrypts Uint8Array instead of uint32[], and the key is also Uint8Array. If you want to encrypt String, you can use xxtea.toBytes(str) to convert String to Uint8Array, when you decrypt Uint8Array, you can use xxtea.toString(bytes) to convert the result to String. Conversion between string and Uint8Array is using UTF8 encoding.

## Usage

```javascript
const xxtea = require('xxtea.js');

var str = "Hello World! 你好，中国！";
var key = "1234567890";
var encrypt_data = xxtea.encrypt(xxtea.toBytes(str), xxtea.toBytes(key));
console.log((btoa(String.fromCharCode.apply(String, encrypt_data))));
var decrypt_data = xxtea.toString(xxtea.decrypt(encrypt_data, xxtea.toBytes(key)));
console.assert(str === decrypt_data);
```

## ChangeLog

1.1.0 update

* Fixed Emoji encode & decode bug.
* Improved Long String encrypt and decrypt.
* Added `encryptToString` and `decryptToString`, for example:

```javascript
const xxtea = require('xxtea.js');

var str = "Hello World! 你好，中国🇨🇳！";
var key = "1234567890";
var encrypt_data = xxtea.encryptToString(str, key);
console.log(encrypt_data);
var decrypt_data = xxtea.decryptToString(encrypt_data, key);
console.assert(str === decrypt_data);
```
