# 页面导航

小程序中页面导航分两种：声明式导航、编程式导航

## 声明式导航：

特点：标签 如<navigator>

### 导航到tabbar    

需要指定url属性和open-type属性，其中：

​	url表示要跳转的页面的地址必须以/开头

​	open-type表示跳转的方式必须为switchTab

### 导航到非tabbar

需要指定url属性和open-type属性，其中：

​	url表示要跳转的页面的地址必须以/开头

​	open-type表示跳转的方式必须为navigate  

navigate可以省略

### 后退导航

如果要退到上一级或多级页面，需要指定open-type属性和delta属性，其中

​	open-type的值必须式navigateBack，表示要进行后退导航

​	delta的值必须是数字，表示要后退的层级

​	delta属性可以省略，默认值为1

## 编程式导航

### 导航到tabbar    

调用wx.switchTab方法可以跳转到tabbar页面，参数如下：

![编程导航到tabbar](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\编程导航到tabbar.png)

### 导航到非tabbar

调用wx.navigateTo方法，可以跳转到tabbar页面，参数同上⬆️

### 后退导航

调用wx.navigateBack方法，可以返回上一页或多级页面，参数如下

![编程导航后退](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\编程导航后退.png)

导航传参

声明式导航传参：url后路径拼接



# 下拉刷新

在页面.js文件中，通过onPullDownRefres()函数即当前页面的下拉刷新事件(触顶)

当下拉刷新后，下拉刷新loading会一直显示，不会主动消失，所以需要手动隐藏下拉刷新的loading效果，此时调用wx.stopPullDownRefresh()可以停止当前页面的下拉刷新

# 上拉触底加载更多

上拉触底距离指的是触发上拉触底事件时，滚动条距离页面底部的距离

可以在全部或者页面.json中配置，通过 onReachBottomDistance属性配置上拉触底的距离 ，默认距离为50px

# 生命周期

生命周期分为两大类：应用生命周期和页面生命周期

![生命周期](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\生命周期.png)

## 生命周期是什么

生命周期：是由小程序框架提供的内置函数，会伴随生命周期，自动按次序执行

生命周期的作用，允许程序员在特点的时间点，执行某些特定的操作，例如在页面刚加载的时候可以在onLoad中初始化页面的数据

### 注意：生命周期强调的是时间端，生命周期函数强调的是时间点

## 应用的生命周期函数

小程序的应用生命周期函数需要在app.js中进行声明

![小程序应用声明周期](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\小程序应用声明周期.png)

## 页面的生命周期函数

![小程序页面给生命周期](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\小程序页面给生命周期.png)

# wxs和javascript的关系

虽然wxs的语法类似于JavaScript，但是wxs和JavaScript是完全不同的语言

## wxs的数据类型

​	number 数值 、string字符串 、Boolean布尔 、object对象、function函数、array数组、date日期、regexp正则

wxs不支持es6以上的语法形式

不支持：let、const、解构赋值、展开运算符、箭头函数、对象属性简写、etc…

支持：var定义变量，普通function函数类似于es5的语法

## 内嵌wxs脚本

wxs代码可以编写在wxml文件中<wxs>标签中，就像JavaScript代码可以编写在html文件中的<script>标签内一样

wxml文件中的每一个<wxs>标签，必须提供module属性，用来指定wxs的模块名，方便在wxml中访问模块中的成员

![内嵌wxs脚本](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\内嵌wxs脚本.png)

# 自定义组件

## 创建组件

![创建组件](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\创建组件.png)

## 局部引用组件

在页面.json文件中引用组件的方式，叫做‘局部引用’

![局部引入组件](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\局部引入组件.png)

## 全局引入组件

在app.json配置文件中引用组件的方式，叫全局引用

![全部引入组件](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\全部引入组件.png)

## 全局引用VS局部引用

当在多个页面频繁使用时，建议用全局引用

当在某个特定的页面中被用到，建议用局部引用

## 组件和页面的区别

虽然他们都由js、json、whml、wxss这4个文件，但是他们的js文件和json文件由明显的不同

组件.json中需要声明component：true属性

组件.js文件中调用的是component（）函数

组件的事件处理函数需要定义在methods节点中

## 组件--样式方面

### 组件样式隔离

默认情况下，自定义组件的样式只对当前组件生效，不会影响到组件之外的UI解构

好处：防止外界的样式影响组件内部的样式

​		   防止组件的样式破坏外界的样式

### 组件样式隔离的注意点

app.wxss中的全局样式对组件无效

只有class选择器会有样式隔离效果，id选择器、属性选择器、标签选择器不受样式隔离的影响

建议：在组件和引用组件的页面中建议使用class选择器，不要使用id、属性、标签选择器

### 修改组件的样式隔离选项

默认情况下，自定义组件的样式隔离特性能够防止组件内外样式互相干扰的问题，但有时，我们希望在外界能够控制内部的样式，此时，可以通过stylesolation修改组件的样式隔离选项

![组件隔离](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\组件隔离.png)

![组件隔离属性值](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\组件隔离属性值.png)

## methods方法

在小程序组件中，事件处理函数和自定义方法需要定义到methods节点中。

## properties属性：

类似与vue中的props  。在小程序组件中，properites是组件的对外属性，用来接受外界传递到组件中的数据

![properties](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\properties.png)

### data和properties的区别

properties属性和data属性的用法相同，他们都是可读可写的，他们的区别在于：

data更倾向于存储组件的私有数据

properties更倾向于存储外界传递到组件中的数据

![data和properties](C:\Users\李林桂\Desktop\p11笔记 作业\day07\笔记总结\img\data和properties.png)

