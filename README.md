# vue源码简析

阅读vue的源码不仅可以深入的理解vue中的问题,还可以学习vue的程序设计;
简析的版本为 v2.5.16

# 前言

目前主要有

- vue响应式原理
- virtual-dom
- template到DOM

注: 每个模块里都包含了对vue源码对应部分的解析,还包含了一个简单的小例子;

# 需要知道的一些javaScript基础

## [flow.js](https://zhenyong.github.io/flowtype/docs/five-simple-examples.html#_)

vue源码中经常能看到 下面的这种代码

![flow.jpeg](https://upload-images.jianshu.io/upload_images/3297464-d84e315425a7c522.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

乍一看还以为是TypeScript,查了一下,是flow.js;关于flow.js的介绍可以直接查看文档[flow.js](https://zhenyong.github.io/flowtype/docs/five-simple-examples.html#_)

代码中使用 flow 进行接口类型标记和检查，在打包过程中移除这些标记。

我们可以看看 vue 的作者 对于 选择 flow 而不是 typescript 的原因

[vue 源码为什么选择 flow 来完成](https://www.zhihu.com/question/46397274)
## Object.protoType

## Object.defineProperty()


## Object.getOwnPropertyDescriptor()

## Object.create()

## Object.keys()

## apply, call

## instanceof
判断是哪种类型的对象

## slice, splice

slice(start, end); 方法可从已有的数组中返回选定的元素。
不会改变原始数组

arrayObject.splice(index,howmany,item1,.....,itemX); 方法向/从数组中添加/删除项目，然后返回被删除的项目。
会改变原始数组;
- index: 必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。
- 必需。要删除的项目数量。如果设置为 0，则不会删除项目。
- item1, ..., itemX: 可选。向数组添加的新项目。

## 闭包
## import, export 的复合写法:
在一个模块之中,先输入后输出同一个模块, import, export 语句可以写在一起;
```js
export { foo, bar } from 'my_module';
// 可以简单理解为
import { foo, bar } from 'my_module';
export { foo, bar };

// 整体输出
export * from 'my_module';
```
上面代码中, import, export 语句可以结合在一起,写成一行,但是需要注意的是,写成一行后, foo和bar实际并没有导入当前模块,只是相对与外转发了这两个接口,导致当前模块不能使用foo和bar

## Set和Map
Set里面没有重复值

## isArray() isObject() Object.isExtensible(object)
isArray(): 是否为数组,返回布尔值
isObject(): 是否为对象
Object.isExtensible(object): 是否可向对象添加新属性