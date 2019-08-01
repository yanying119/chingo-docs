## 公共组件

### 目录位置（src/components/common）

#### 一、高德地图 Map

> 功能：引入高德地图

> props： element-id 地图的 id(非)， coordinate 地图中心点坐标(非) ，readonly 是否只读 默认 false(非)

> 事件：setCoordinate 获取点击的位置

**用例：**

```javascript
<template>
  <Map element-id='map' :coordinate="3212321,13213" :readonly="false" @setCoordinate="setCoordinate"/>
</template>
<script>
  import Map from '../common/map.vue';
  export default {
    components:{Map},
    methods:{
      setCoordinate(lng, lat){
        console.log(lng, lat)
      }
    }
  }
</script>
```

#### 二、百度编辑器 UE

> 功能：引入高德地图

> props：element-id 编辑器的 id(非)， content 编辑器内容(必填)， ueConfig 编辑器配置(非)

> 事件：setNewContent 编辑器内容变化的回调(必填)

**用例：**

```javascript
<template>
  <UE element-id='ue' :content="ueContent" :ueConfig="ueconfig" @setNewContent="setNewContent" />
</template>
<script>
  import UE from '../common/ue.vue';
  export default {
    components:{UE},
    data(){
      return {
        ueconfig:{},
        ueContent:"<div>111<div>"
      }
    },
    methods:{
      setNewContent(content){
        this.ueContent = content;
      }
    }
  }
</script>
```

#### 三、模态框

> 功能：全局模态框，用于弹出一些提示信息。

> 参数：一个对象 {show: false, title: '系统提示', content: '', onOk: function() { return false;}}

**用例：**

```javascript
<template></template>
<script>
  export default {
    data(){
      return {}
    },
    methods:{
      openModal(){
        this.$store.commit("setModal",{
          // 模态框显示与否  false 关闭 true 显示
          show: false,
          // 模态框的头部文字
          title: '系统提示',
          // 提示的内容
          content: '',
          onOk: ()=>{
            // 点击确定按钮所执行的事件
          }
        })
      }
    }
  }
</script>
```

#### 四、加载中

> 功能：显示一个加载状态。

> 参数： ture or false

**用例：**

```javascript
<template></template>
<script>
  export default {
    data(){
      return {}
    },
    methods:{
      handler(){
        // 显示加载中
        this.$store.commit("setLoading",true)
        // 关闭加载中
        this.$store.commit("setLoading",false)
      }
    }
  }
</script>
```

#### 五、列表搜索框组件 Seacher

> 功能：用于列表搜索条件太多时，可以点击展开搜索条件。

> props：show true or false， setShow 父级控制搜索框显示隐藏的事件

> slot : left 显示在控制按钮左侧的内容，right 显示最右侧的内容

> **用例：**

```javascript
<template>
<Layout>
  <Content>
    <Card>
      <Search :show="show" :setShow="setShow">
        <Button slot="left">显示在左边</Button>
        <Button slot="right">显示在右边</Button>
        <!--这里填写其他的搜索条件-->
        <From>
          <FormItem>
            <Input v-modal="keywords"/>
          </FormItem>
        </Form>
      </Search>
      <!--下面是列表-->
    </Card>
  </Content>
</Layout>
</template>
<script>
  import Search from '../common/search.vue';
  export default {
    data(){
      return {
        show:false
      }
    },
    components:{Search},
    methods:{
      setShow(bool){
        this.show = bool
      }
    }
  }
</script>
```

#### 六、权限点按钮 list-button

> 功能：用于放置带有权限判断的操作按钮或者链接。

> props：rule [String]对应的权限点 routeName，usable[Boolean] 是可用状态 还是禁用状态 true or false，to 链接地址同 router-link 的属性 to

> slot : 标签之间的内容 操作是显示按钮还是链接 或者一句话（合法的 html）

> 事件 : on-click 点击事件 有 to 的情况先执行 to 跳转

> **用例：**

```html
<template>
  <!-- 操作链接 -->
  <list-button rule="xxx" :usable="a==b" :to="{name:'xxx'}">名称</list-button>
  <!-- 操作按钮 -->
  <list-button rule="xxx" :usable="a==b" @on-click="doSomething">
    <button type="primary">按钮名称</button>
  </list-button>
</template>
```

#### 上传文件 upload-file

> 功能：用于上传文件或者图片

> props：files[Array,Object] 要上传的文件，isImage[Boolean] true 上传图片 false 上传文件

> 事件 : on-success 文件上传成功的钩子，on-delete 图片删除成功的钩子

> **用例：**

```html
<template>
  <upload-file :isImage="true" files="files" @on-success="uploadSuccess" @on-delete="deleteFile" />
</template>
<script>
  export default {},
  methods:{
    data(){
      return {
        // 父页面处理图片 数组或者对象
        files:[]
      }
    },
    methods:{
      uploadSuccess(){},
      deleteFile(){},
    }
  }
</script>
```
