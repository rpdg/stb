## 不再复杂的EPG页面开发
#### EPG运行于电视端，与我们所接触的前端(手机端、电脑端)有一定差异。体现为复杂的焦点管理，调试成本很高，播放器以及各个盒子之间兼容性问题。都在我们编码前无形增加难度。甚至于一天写好所有功能，要花两到三天去调试程序BUG，这几乎是无法接受的状态，恰恰也是不可避免的问题。
#### 基于这样的初衷想过一些方案，比如利用主流框架优势(React、Vue)来简化开发难度，通过TypeScript 引入模块化方案。通过前端OOP合理组织代码。有些方案可行，盒子运行内核由各大厂商(华为、中兴、海信、烽火)等。盒子版本有2k、4k，由于这些客观原因，导致主流框架无法运行。
#### React 具有视图层复用，单项数据流等优势，对于EPG开发来说是一种福音。读了 [React 设计思想](https://github.com/react-guide/react-basic) 以及各个大神解析的 React 实现思路。完成了具备（状态机、虚拟DOM、组件化、子父组件）等概念的TV版React 框架且在各大IPTV专区完美运行，当然还有非常大改进空间。不过现有框架的优势也很明显，因此建议大家在了解后采用他，并提出自己宝贵改进建议。

## 框架结构与源码解析
#### 文件结构

#### 页面生命周期

#### 基础库

#### 焦点引擎

#### React

#### 播放器

#### 辅助命令
##### 为了更好的组织代码以及充分发挥模块化优势，采用 webpack + gulp 模式尽可能简化开发难度。webpack 实现打包以及模块依赖，gulp 则提供快捷创建页面等需求

###### 启动编译监听
>>
``` javascript
yarn start:dev
```

###### 启动服务预览
>> ###### 注意：需要等编译监听完全启动后再启动服务预览
``` javascript
yarn start:ser
```


## 起步
>>#### [我的第一个EPG程序（一）：初始化项目环境](https://github.com/442331311/stb/issues/3)
>>#### [我的第一个EPG程序（二）：Hello EPG!](https://github.com/442331311/stb/issues/4)
>>#### [我的第一个EPG程序（三）：我的第一个EPG程序（三）：焦点管理](https://github.com/442331311/stb/issues/5)
>>#### [我的第一个EPG程序（四）：...]()

## EPG开发记录
#### EPG页面运行于IPTV平台，其特殊性导致相关开发技术与人员是小众群体，总结了以下开发记录可有效避免一些常规问题
>>[EPG开发日志（一）：盒子与浏览器差异](https://github.com/442331311/stb/issues/1)

## 开发体验优化
#### [开发体验优化（一）：清除缓存之本地服务]()

# 改进
- 去掉 BOOTSTRAP 默认 CSS3 属性，不可控属性影响盒子性能
- 启用本地node 服务 0 缓存，盒子指向本地。可实现不重启盒子便更新代码，但是必须在局域网内

# BUG
- 优化 API 缓存
- 两分钟快进会回到快进期初位置在跳到快进点。流播放是正常
- 播放器结束事件优化，采用接口的（考虑）可能存在兼容性。暂时不改
- 阴影算法需要包含最近元素四个角的运算
- componentWillUpdate 有时未正常触发;加载完毕后再去更新，render 在这之前执行了
- loadFocus 位置调整
- 无状态组件或有状态组件，在任何情况下必须返回父节点，否则导致异步更新无法加载情况
- 
- dom 渲染异常(部分组件之后所有未渲染，更新状态后某个组件未渲染)
- React 渲染节点不允许节点元素存在 null 需要进行字符串转换
- 无状态组件和有状态组件必须返回不变根容器，无状态组件建议使用普通函数直接返回 jsx 节点；灵活性更强

# 优化建立
- React 组件 css + js 解决方案
- 去掉所有默认样式，提升运行性能
- 修复ts 与 less 图片加载路径
- 状态和业务逻辑放到单独模块进行管理，渲染模块仅复杂渲染
- 常用组件封装（单个移动+异步加载数据）

# 未实现
>#### 网络请求兼容 axios 方式

# 相关项目
- anhui-戏曲（2017）
- neiment-环球（2017）
- yunnan-4k（2017）
- anhui-猜灯谜（2018）
- anhui-送祝福（2018）
- neiment-天翼（2018.3）
- anhui-聚合（2018.5）
- yunnan-618活动（2018.6）
- anhui-世界杯活动（2018.6）
- shanxi-少儿（2018.7）
- anhui-体育（2018.9）
- guizhou-电竞（2018.11）
- anhui-直播活动（2018.11）
- guangxi-教育（2018.11）
