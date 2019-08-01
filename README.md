# vueApp

> vue 应用基础构建模版项目，其中包含模块如下:

- 用户模块
- 菜单（权限点）模块
- 角色模块
- 系统设置
- 公共代码模块
- 左侧栏模块
- 页头 页尾
- 404 页面

## 一、构建新项目

```bash
# download
git clone https://git.chingo.net/vueApp/vue-template.git
# 安装依赖
npm install
# 本地服务器运动地址 http://localhost:8081
npm run dev
# 生产模式打包
npm run build--prod
# 自动化测试模式打包
npm run build--test
```

## 二、[项目目录介绍](CATALOG.html)

```bash
# 项目源码目录
/src
# 静态资源
/src/assets
# vue页面组件
/src/components
# 前端路由配置
/src/router
# vuex目录
/src/vuex
# 配置文件
/src/config.js
 # 项目入口文件
/src/main.js
# 入口页面
/src/main.vue
```

## 三、[全局变量使用方法](COMMONJS.html)

```javascript
// 全局变量定义在main.js里面

Vue.prototype.config = config; // 配置文件 在.vue 使用  this.config.xxx  就能使用xxx配置
Vue.prototype.commonMethods = commonMethods; // 公共函数 在.vue 使用  this.commonMethods.xxx  就能使用xxx函数
Vue.prototype.userInfo = JSON.parse(commonMethods.getLocalData('dataThree', true, '{}')); // 用户信息 登陆后有效。在.vue 使用  this.userInfo获取
```

## 四、应用到的插件

- [vue][1] [vuex][2] [vue-router][3]
- [moment][4]
- [iview][5]
- [crypto-js][6]

[1]: https://cn.vuejs.org/v2/api/
[2]: https://vuex.vuejs.org/zh-cn/
[3]: https://router.vuejs.org/zh-cn/
[4]: http://momentjs.cn/docs/
[5]: https://www.iviewui.com/docs/guide/install
[6]: https://www.npmjs.com/package/crypto-js
