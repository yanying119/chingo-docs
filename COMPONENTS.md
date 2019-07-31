## 公共组件

### 目录位置（src/components/common）

#### 一、高德地图

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
  },
  methods:{
    setCoordinate(lng, lat){
      console.log(lng, lat)
    }
  }
</script>
```

#### 二、百度编辑器

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

#### 五、列表搜索框组件

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
