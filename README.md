<div>
    <h1 align="center"><code>relation-network-graph</code></h1>
    <p align="center">
        <strong style="color:red">数据图谱初始化、力导向计算、节点布局、渲染</strong>
    </p>
    <p>
        智能图谱解决方案，关系图谱，网络图谱，D3force力导向图，知识图谱可视化，是关系网络中实体与关系与实体的表示，是将复杂的信息通过计算处理成能够结构化表示的数据
    </p>
</div>

## 应用场景

>人物关系、互联网关系、图书情报、知识产品、产业链图谱、企业图谱、医疗、汽车等

![](https://github.com/haojiey/relation-network-graph/blob/master/example/assets/images/graph.png)

![](https://github.com/haojiey/relation-network-graph/blob/master/example/assets/images/all.png)

## 在线示例

### 基础展示

<https://haojiey.github.io/relation-network-graph/example/index.html>

### 可操作性功能展示

<https://haojiey.github.io/relation-network-graph/example/page/operate.html>

![](https://github.com/haojiey/relation-network-graph/blob/master/example/assets/images/operate.png)

### 自定义可操作性功能展示

<https://haojiey.github.io/relation-network-graph/example/page/operateCustom.html>

![](https://github.com/haojiey/relation-network-graph/blob/master/example/assets/images/customoperate.png)

### 颜色大小配置展示

<https://haojiey.github.io/relation-network-graph/example/page/colorSize.html>

### 特定范围内展示

<https://haojiey.github.io/relation-network-graph/example/page/range.html>

### 大数据量展示

<https://haojiey.github.io/relation-network-graph/example/page/bigData.html>


## 安装

### 使用 npm 或 yarn 安装

```bash
$ npm install relation-network-graph --save
```

```bash
$ yarn add relation-network-graph
```

### 使用静态资源

```bash
引入静态文件dist/relation-network-graph.js
```

## 文档

### 使用方式

```js
import { createContainer } from 'relation-network-graph';
new createContainer(options:ContainerConfig)
```

### 配置说明

`ContainerConfig`：

 成员 | 说明 | 类型 | 是否必须 | 默认值
---|---|---|--- |---
width | 容器宽度 | `number` | 是 | 1000
height | 容器高度 | `number` | 是 | 1000
containerName | 所在容器元素使用id | `string` | 是 | 
nodes | 节点数据 | `Node[]` | 是 | []
links | 节点间的关系数据 | `Link[]` | 是 | []
benchmark | 数据基准点以数据的什么属性为基准 | `string` | 否 | id
background | 容器背景色 | `string` | 否 | #F7FAFC
isShowMask | 选中某个节点时其他节点是否出现暗淡效果 | `boolean` | 否 | true
isCustomMouse  | 是否支持节点自定义mouse事件 | `boolean` | 否 | false
toolbarData | 点击节点周围出现扇形区域进行更多功能的操作`（删除、连线、收起、展开等）` | `toolbarData[]` | 否 | [toolbarData](/example/common/toolbarData.js)
colors | 节点颜色集合 | `string[]` | 否  | [colors](/example/common/colors.js)
activeColors | 移入节点时高亮效果 | `string[]` | 否 | [activeColors](/example/common/activeColors.js)
nodeClick | 点击节点时触发相应函数 | `Function(Node)` | 否 | 
nodeMouseover | 移入节点时触发相应函数(搭配isCustomMouse使用) | `Function(Node)` | 否 | 
nodeMouseout | 移除节点时触发相应函数(搭配isCustomMouse使用) | `Function(Node)` | 否 | 
nodeMove | 节点内移动时触发相应函数 | `Function(Node)` | 否 | 
linkClick | 点击节点间关系线时时触发相应函数 | `Function(Link)` | 否  | 
zoomOptions | 容器缩放配置 | `zoomOptions` | 否  | 0.5-1.5
linkOps | 关系线配置 | `linkOps` | 否  | 
layout | 控制节点的显示，在特定范围内展示 | `layout` | 否  | 

`Node[]`:

 成员 | 说明 | 类型 | 是否必须 | 可用值
---|---|---|--- |---
id | 唯一id | `string｜number` | 是 | 
name | 节点名 | `string` | 是 | 
color | 节点颜色 | `number` | 否 | [1,2,3]等
size | 节点大小 | `number` | 否 |  [1,2,3]
shape | 节点形状 | `string` | 否 | 'circle'|'rect'｜'ellipse '
props | 属性 | ` Array<any>` | 否 | 
hide | 是否隐藏 | `boolean` | 是 | false|true
isExtendedState | 是否是扩展状态 | `boolean` | 是 | false|true

`Link[]`

 成员 | 说明 | 类型 | 是否必须 | 可用值
---|---|---|--- |---
id | 唯一id | `string` | 是 | 
label | 关系名称 | `string` | 是 | 
hide | 是否隐藏 | `boolean` | 是 | false|true
color | 关系颜色 | `string` | 是 |  ['1','2','3']等
label | 关系名称 | `string` | 是 | 
source | 源点基准id | `string｜number` | 是 | 
target | 终点基准id | `string｜number` | 是 | 
sourceRadius | 点的半径 | `number` | 是 | 
targetRadius | 点的半径 | `number` | 是 | 
value | 关系线的粗细 | `number` | 是 | 
color | 线条颜色 | `number` | 否 | [1,2,3]等
props | 属性 | ` Array<any>` | 否 | 

`zoomOptions`
 成员 | 说明 | 类型 | 是否必须 | 可用值
---|---|---|--- |---
minScale | 最小值 | `number` | 是 | 0-10
maxScale | 最大值 | `number` | 是 | 0-10

`linkOps`
 成员 | 说明 | 类型 | 是否必须 | 可用值
---|---|---|--- |---
stroke | 关系线的颜色 | `string` | 是 | 
stroke-opacity | 关系线的透明度 | `number` | 是 | 0-10


`layout`
 成员 | 说明 | 类型 | 是否必须 | 可用值
---|---|---|--- |---
x | x轴缩小范围大小 | `number` | 是 | 
y | y轴缩小范围大小 | `number` | 是 | 
simulation | y轴作用力 | `number` | 否 | 
distance | 关系线长度 | `number` | 否 | 
force | 是否开启特定范围内展示 | `number` | 是 | 

## 支持环境
| <img src="https://pics7.baidu.com/feed/4bed2e738bd4b31c2542220f4c6705759f2ff840.jpeg?token=f18b7f2b7df0e8f00a53fa110318a8dd" alt="IE / Edge" width="24px" height="24px" /></br>IE / Edge | <img src="https://bkimg.cdn.bcebos.com/pic/5fdf8db1cb134954092380157c048558d109b3dedc22?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg" alt="Firefox" width="24px" height="24px" /></br>Firefox | <img src="https://www.google.cn/chrome/static/images/chrome-logo.svg" alt="Chrome" width="24px" height="24px" /></br>Chrome | <img src="https://bkimg.cdn.bcebos.com/pic/2f738bd4b31c8701a18b05fd5f34892f0708283851de?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg" alt="Safari" width="24px" height="24px" /></br>Safari | <img src="https://bkimg.cdn.bcebos.com/pic/f9198618367adab4ee604c1183d4b31c8701e434?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg" alt="Opera" width="24px" height="24px" /></br>Opera 
|---|---|---|---|---
|10+ | 52+ |15+|5.1+|15+

