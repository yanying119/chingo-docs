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
