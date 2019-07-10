# 路由设置

## 目录位置(src/router/routers.js)

### 添加一个新路由

```script
  export default [
    {
      path: '/',
      name: 'Index',
      component: () => import('@/components/index'),
      meta: {
        title: '首页',
        noCheckRule: true
      }
    },
    {
      path: '/new',     // 路由访问path
      name: 'Index',    // 路由名称 唯一性  菜单权限配置里面前端路由名称就是这个字段
      component: () => import('@/components/new.vue'),   // 对应的.vue文件
      meta: {              // 一些其他的信息
        title: '新路由',   // 路由显示在网页title上的名称以及面包屑的名称
        noCheckRule: true,  //不检查页面权限的页面
        fullScreen: true,   //没有头部左侧菜单的页面
        noLogin:true,   //不需要登录的页面
        breadcrumb: [   // 如果此路由不在左侧菜单上 但是又要高亮一个菜单 配置此选项，这种情况进入这个路由，左侧用户管理菜单高亮
          {
            name: '用户管理',
            url: '/user'
          }
        ]
      }
    }
  ]
```
