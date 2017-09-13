# 密码学

* 密码学（cryptography）是互联网安全的基础。
* 密码体系的安全性只在于秘钥的保密性，而不在加密算法的保密性。
* 优秀的加密算法是可公开的，经得起考验的。
* 优秀的加密算法的衡量标准：我告诉你密文是什么，我是怎么加密的，反正你就是解不开！
* 理论上，任何加密技术都可以破解的，只是有些算法破解的难度超乎你想象。
* 只要破解一个密文得到的利益小于破解的成本，这个密码就是安全的。
* 木桶原理

## 常见术语

* 明文：没有加密的文字。
* 密文：加密后的文字。
* 秘钥（mì yào）：加密时用到的密码。
* 加密：通过加密算法，使用秘钥对明文进行处理，得到密文。
* 解密：通过解密算法，使用秘钥从密文获得明文。

## 对称加密

对称加密（Symmetric Cryptography）是一种单钥密码系统的加密方式，所谓“单钥”，是指加密和解密采用同一个秘钥。

公钥和私钥是不一样的，不能由其中一个密钥推导出另一个密钥。

常见的对称加密算法：

* DES（Data Encryption Standard，数据加密标准）
* 3DES（Triple DES，三重数据加密算法）：对明文进行三次 DES 机密。
* AES（Advanced Encryption Standard，高级加密标准）

## 非对称加密



对称加密是很安全的，其安全性依赖于秘钥。

我们可以假设一个场景：A 需要发送某段信息给 B。

如果使用对称加密，通常做法是 A 对信息进行加密，将密文和秘钥告诉 B。现在遇到的难题是：如何安全地把秘钥告诉 B。

1. 私下见面，把秘钥告诉 B。这是一种成本很高的做法，有时候还不具备可行性。
2. 对秘钥进行加密再传输。本质上没有解决问题，秘钥的秘钥怎么传输？

这还只是两个人之间的通讯，当通讯的人数增多时，比如 N 个人之间需要两两通讯时，就会变得很复杂。

为了解决这个难题，诞生了非对称密码体系（也称作公钥密码系统）。与对称加密相对，非对称加密采用公钥（public key）和私钥（private）的其中任意一个加密，另一个解密。它有以下特点：

* 公钥的私钥是一对的，并且是不同的。
* 不能由公钥推出私钥，反之亦然。

有了公钥密码体系，对于上述的场景，一般可以这么做：

1. B 通过非对称加密算法生成秘钥和公钥，并将公钥公开。
2. A 通过 B 的公钥将明文加密，得到密文，把它传输给 B。
3. B 得到密文后，通过私钥解密得到明文。

一般而言，密码体系的安全性在于秘钥的保密性，公钥密码体系解决了传统密码系统的秘钥传输难题。

缺点：由于非对称加密算法的复杂度较高，因此非对称加密的速度远没有对称加密算法快。

常见的非对称加密算法：

* RSA

## 散列算法

散列算法也叫做哈希函数，我们可以把它当做一个字符串处理函数，它接收一个字符串参数，返回一个字符串。

```javascript
let messgae = hash(string)
```

一个好的函数哈希函数有以下特点：

* 允许参数 `string` 不同的长度。
* 返回的字符串 `message` 长度固定。
* `hash` 函数的实现尽可能简单高效。
* 知道 `message` 无法推出 `string` 是什么。
* 同一个 `string`，返回的 `message` 一定是相同的。
* 对于不同的参数 `string`，返回的 `message` 一定是不同的。

散列算法有很多种实现，比较常用的有：MD4、MD5 SHA-1、SHA-256、sha512 等。

## 应用

## 文件

由于哈希函数具有这些特性，常用于文本内容的校验，用来判断文本或者文件是否内容一致。

在网盘上传文件时，有时候会“秒传”，几个 G 大小的文件，一秒钟就上传完了。事实上，这个文件并没有被上传到服务器。这里，就用到了哈希函数算法。

当用户上传文件时，服务器会计算文件的哈希值，如果数据库不存在这个哈希值，那么就把文件上传到服务器，并且保存哈希值到数据库；如果数据库存在这个哈希值，就说明其他用户已经上传过一个一模一样的文件，就无需再重复上传，节省服务器空间。

## 数据库用户密码安全

数据库密码明文存储是很不安全的。很多大的互联网公司都有被“拖库”的黑历史，何况是小网站。而且，即使网站没有被恶意入侵，明文密码也可能被不怀好意的管理员或运维人员拿到。

通常的做法是，把用户的密码的哈希值保存到数据库而不是明文密码。这样做的好处是，密码相对会安全点。

仅仅使用哈希值，还是不够安全的。尽管无法从哈希值逆推出原密码，但是可以暴力破解。

我们可以准备这样的一张表，把常见的密码及其哈希值都保存起来。

```text
123456: e10adc3949ba59abbe56e057f20f883e
88888888: 8ddcff3a80f4189ca1c9d4d902c3c909
admin: 21232f297a57a5a743894a0e4a801fc3
abc123: e99a18c428cb38d5f260853678922e03
1314520: b206e95a4384298962649e58dc7b39d4
1: c4ca4238a0b923820dcc509a6f75849b
2: c81e728d9d4c2f636f067f89cc14862c
...
```

我们把这样的表叫做彩虹表。通常彩虹表是很大的，一般有几十 G 到几百 G。有了彩虹表，就可以较容易地破解简单的密码。

也有很多在线的破解网站，比如 [http://www.cmd5.com/](http://www.cmd5.com/)，可以破解简单的哈希值。这些网站的原理，其实就是彩虹表。

为了应对彩虹表，简单的方法就是增加密码的长度和复杂度。但是要限制用户必须输入复杂的密码是不可行的。通常的做法是“加盐值”。

所谓的盐值（Salt），其实就是一段随机的字符串，它的作用是增加密码的复杂度。最后存入数据库的是 `hash(salt + password)` 和 `salt`。




拖库：数据库数据被盗。
撞库：将盗取的数据库的登陆信息在其他网站尝试登陆。


信息指纹
    



破解密码的成本

# 数字签名

数字签名（digital signature）

数字证书（digital certificate）

A 要和 B 通讯，一般是这样做的：

1. A 将信息加密，把密文发给 B，并公开公钥。
2. B 收到信息，用 A 的公钥解密，得到明文。






