# Vue全家桶模拟去哪儿网 WebApp

基于 Vue+ vuex + vue-router + vue-axios +better-scroll + Scss + ES6 等开发的 WebApp，UI 界面参考了去哪儿网。

## 预览

部署地址：http://47.104.204.20/

## 安装运行与打包

``` bash
git clone git@github.com:Nonentityboy/Vue2.5-qunar.git

npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

## 首页

![menu](http://47.104.204.20/img/qunar/menu.png)


## 详情页与城市选择页

![detail](http://47.104.204.20/img/qunar/detail.png)
![citys](http://47.104.204.20/img/qunar/citys.png)

## 学习开发一个 Vue 全家桶项目，让自己更熟练的使用 Vue 全家桶、模块化开发、ES6 等等知识，提高自己的技术能力。

## 技术栈

* Vue：用于构建用户界面的 MVVM 框架
* Vue-router：为单页面应用提供的路由系统
* axios：用来请求后端数据，谁用谁知道
* Vuex：集中状态管理，实现多个组件之间共享数据
* SCSS：css 预编译处理器
* ES6：新一代的语法规范

## 其他工具

* Vue-lazyload：实现图片的懒加载，优化页面性能节省用户流量
* better-scroll：解决移动端各种滚动场景需求的插件，使移动端滑动体验更加流畅
* fastcliclk：解决移动端300ms延迟
* iconfont：阿里图标库
* borderCSS：解决1像素边框问题，防止高分辨率手机将1px像素渲染成2或3单位物理像素
* VueAwesomeSwiper：功能强大，可以实现不同效果的轮播功能

## 项目准备

* 导入了reset.css，初始化了项目的一些基本样式。
* 因为是移动app，所以需要在index.html里面需要对meta标签进行修改 
```
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no">
```
intial-scale:页面首次被显示是可视区域的缩放级别，取值1.0则页面按实际尺寸显示，无任何缩放 maximum-scale=1.0, minimum-scale=1.0;可视区域的缩放级别， maximum-scale用户可将页面放大的程序，1.0将禁止用户放大到实际尺寸之上。 user-scalable:是否可对页面进行缩放，no 禁止缩放

## 实现功能
### 首页列表
使用axios获取数据，然后渲染到页面上。
城市列表页
搜索功能：在这里使用到了定时器实现函数节流，提高性能。

侧边栏拖拽页面联动：同样是使用到函数节流。主要思路是先获取字母A到顶部的距离，点击的时候触发事件，计算点击的点的坐标减去顶部的距离，获取到的数据除以每个字母的高度，然后向下取整，得到对应字母的索引，将数据传递给父组件再转发给列表显示组件，实现两个组件之间的联动。

### 城市选择
使用vuex传递城市选择页面和首页当前城市定位城市的数据，并且使用localStorage存储用户的选择，最好使用try catch将其包裹起来，防止浏览器关闭其功能导致代码无法运行。

### 详情页面
详情页面使用到了递归组件，如果需要渲染的数据中，存在children的子数组，需要显示多级的时候则需要使用到。这种场景算是第一次遇到，敲黑板记笔记了。

## 学到了什么
* 防止页面抖动：给每一个页面的区域固定一个高度，防止网络问题，造成页面的抖动,padding-bottom的值主要是根据宽高比计算的。确实是JS体现技术深度，CSS体现经验程度
```
.wrapper{
    overflow: hidden;
    background: #fff;
    width: 100%;
    height: 0;
    padding-bottom: 31.25%;
}
```

* 网页的默认字体：设置默认字体为font-size为50px，那么在换算成为rem单位的时候，直接乘以0.02就可以了。这个可能不同人会有不同习惯，也有人设置成62.5%，也没有绝对的好坏之分。 如果有些方案无法具体确定下来的话，其实可以参考其他大厂的解决方案，因为用到的大都是前沿的、兼容性好点的技术，比如这个方案淘宝系和网易家的解决方案就不一样

* 生命周期：这个说来是最羞耻的，平时学习以为只有常见的8个钩子函数，但是直到这里才发现漏了activated、deactivated以及vue2.5新增的errorCaptured。具体看官网文档吧，挺仔细的。

### 写在最后
本人是2021届毕业生，打算将之前做过的项目都进行部署到服务器里，以为春招做准备。
有任何问题可联系本人：13891316148（同微信）。
