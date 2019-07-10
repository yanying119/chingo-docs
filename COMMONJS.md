## commonMethods 全局方法简介

### 一、emitAjax

> 功能：发送网络请求 Ajax

> 参数：opt 数据类型：{}

> 返回值： 无

**用例：**

```javascript
this.commonMethods.emitAjax({
  path: '', //请求地址
  type: 'GET', //请求方式 大写
  data: null, // 请求数据
  dataType: 'common', //文件上传还是普通数据交互 值为file是上传文件
  headers: null, // 头部信息
  responseType: null, //文件下载 值一般blob
  async: true, //true异步  false 同步
  success: function() {}, //code200执行的函数
  error: function() {}, //不是code200 执行的函数
  progress: null // 监听上传进度
});
```

### 二、setLocalData

> 功能：设置本地缓存（localStorage）

> 参数：opt 数据类型：{} 对象的 key value 对应的就是 localStore 的 key value

> 返回值： 无

**用例：**

```javascript
// 储存数据名称a 存的值为'bbb' 可同时设置多个
this.commonMethods.setLocalData({
  a: 'bbb'
});
```

### 三、getLocalData

> 功能：获取本地缓存数据（localStorage）

> 参数：key 储存数据名称， ispassword 是否需要解密数据， defaultData 如果没有找到数据返回的值

> 返回值： 字符串

**用例：**

```javascript
// 获取数据a a的值是经过加密的所以要解密 如果没有获取到a 则返回'ccc'
const string = this.commonMethods.getLocalData('a', true, 'ccc');
```

### 四、delLocalData

> 功能：删除本地缓存数据（localStorage）

> 参数：array 可以是'all' 也可以是粗存数据名称数组

> 返回值： 无

**用例：**

```javascript
// 删除所有数据
this.commonMethods.delLocalData('all');
// 删除a b 两个数据
this.commonMethods.delLocalData(['a', 'b']);
```

### 五、setCookie

> 功能：设置 cookie

> 参数：name 名称， value ，cookie 的值 date 有效时间（天）

> 返回值： 无

**用例：**

```javascript
// 设置名称为a的cookie 有效期 1天
this.commonMethods.setCookie('a', '1', 1);
```

### 六、getCookie

> 功能：获取 cookie

> 参数：name 名称

> 返回值： cookie 的值

**用例：**

```javascript
// 获取cookie a
const cookie = this.commonMethods.getCookie('a');
```

### 七、delCookie

> 功能：删除 cookie

> 参数：name 名称

> 返回值： 无

**用例：**

```javascript
// 删除cookie a
this.commonMethods.delCookie('a');
```

### 八、keySetPassword

> 功能：数据加密(ase)

> 参数：opt String & Object

> 返回值： 无

**用例：**

```javascript
// 字符串加密
this.commonMethods.keySetPassword('a');
// 对象数组加密，会转化成Json 字符串
this.commonMethods.keySetPassword({ a: 'b' });
```

### 九、keyGetPassword

> 功能：解密

> 参数：string 加密后的字符串

> 返回值： 解密后的字符串

**用例：**

```javascript
// 返回的是解密后的字符串
const string = this.commonMethods.keyGetPassword('afsdfsdf');
```

### 十、setBase64

> 功能：base64 加密

> 参数：string 要加密的字符串

> 返回值：加密后的字符串

**用例：**

```javascript
// 返回的是加密后的字符串
const string = this.commonMethods.setBase64('afsdfsdf');
```

### 十一、getBase64

> 功能：base64 解密

> 参数：string 加密后的字符串

> 返回值：解密后的字符串

**用例：**

```javascript
// 返回的是解密后的字符串
const string = this.commonMethods.getBase64('afsdfsdf');
```

### 十二、downFile

> 功能：文件流下载

> 参数：blob 后台返回的文件流 ，fileName 下载后保存的文件名称

> 返回值：无

**用例：**

```javascript
// 下载word文件
this.commonMethods.downFile(blob, 'aaa.doc');
```

### 十三、arrayIndexOf

> 功能：获取数组的索引

> 参数：array 目标数组， value 要对比的值， key 如果目标数组是个对象数组要对比的 key 值

> 返回值：value 在 array 中的索引

**用例：**

```javascript
// 普通数组
const index = this.commonMethods.arrayIndexOf([1, 2, 3], 3); // index=2
// 对象数组
const index = this.commonMethods.arrayIndexOf([{ a: 1 }, { a: 2 }], 2, 'a'); // index=1
```

### 十四、getTypeOf

> 功能：获取具体数据类型 比 typeof 更详细

> 参数：data 目标数据

> 返回值：typeof 数据类型

**用例：**

```javascript
const typeString = this.commonMethods.getTypeOf(1); // number
const typeString = this.commonMethods.arrayIndexOf('1'); // string
const typeString = this.commonMethods.arrayIndexOf({}); // object
const typeString = this.commonMethods.arrayIndexOf([]); // array
const typeString = this.commonMethods.arrayIndexOf(function() {}); // function
const typeString = this.commonMethods.arrayIndexOf(true); // boolean
const typeString = this.commonMethods.arrayIndexOf(null); // null
const typeString = this.commonMethods.arrayIndexOf(undefined); // undefined
const typeString = this.commonMethods.arrayIndexOf(blob); // blob
const typeString = this.commonMethods.arrayIndexOf(new FormData()); // formdata
const typeString = this.commonMethods.arrayIndexOf(new Date()); // date
```

### 十五、hasLogin

> 功能：判断是否登录

> 参数：无

> 返回值：boolean true or false

**用例：**

```javascript
const isLogin = this.commonMethods.hasLogin();
```

### 十六、isPhone

> 功能：是否是正确手机号

> 参数：phone 手机号

> 返回值：boolean true or false

**用例：**

```javascript
const isPhone = this.commonMethods.isPhone();
```

### 十七、isMail

> 功能：是否是正确邮箱

> 参数：mail 邮箱

> 返回值：boolean true or false

**用例：**

```javascript
const isMail = this.commonMethods.isMail();
```

### 十八、MD5

> 功能：MD5 加密

> 参数：string

> 返回值：加密后的数据

**用例：**

```javascript
const md5 = this.commonMethods.MD5().toString();
```

### 十九、hasHanderRule

> 功能：判断是否有操作权限

> 参数：操作点的 routeName

> 返回值：boolean true or false

**用例：**

```javascript
// 是否有登录权限
const havaLogin = this.commonMethods.hasHanderRule('routeName');
```
