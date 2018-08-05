# TGFE面试题整理(beta0.1)

### webpack与grunt、gulp的不同？
三者都是前端构建工具，grunt和gulp在早期比较流行，现在webpack相对来说比较主流，不过一些轻量化的任务还是会用gulp来处理，比如单独打包CSS文件等。
> grunt不了解，谁补充一下吧 TODO

gulp是基于任务和流（Task、Stream）的。类似jQuery，找到一个（或一类）文件，对其做一系列链式操作，更新流上的数据，
整条链式操作构成了一个任务，多个任务就构成了整个web的构建。

webpack是基于入口的。webpack会递归解析入口所需要加载的所有资源文件，然后不同的Loader来处理不同的文件，Plugin来扩展webpack功能。

所以总结一下：
 * 从构建思路来说
 
    gulp需要开发者将整个前端构建过程拆分成对个Task，并合理控制所有Task的调用关系
    webpack需要开发者找到入口，并清楚对于不同的资源使用什么Loader做何种解析或加工
 * 对于知识背景来说
 
    gulp更像后端开发者的思路，需要对于整个流程了如指掌
    webpack更倾向于前端开发者的思路


### 与webpack类似的工具还有哪些？谈谈你为什么最终选择（或放弃）使用webpack？
同样是基于入口的打包工具还有以下几个主流的：
 * webpack
 * rollup
 * parcel
 
 
 ##### 从应用场景上来看：
 * webpack适用于大型复杂的前端站点构建
 * rollup适用于基础库的打包
 * parcel适用于…… 我也不知道
 



### 有哪些常见的Loader？他们是解决什么问题的？



### 有哪些常见的Plugin？他们是解决什么问题的？



### Loader和Plugin的不同？



### 如何配置多个入口文件？



### 如何提高webpack的构建速度？



### webpack的构建流程是什么?从读取配置到输出文件这个过程尽量说全



### 是否写过Loader和Plugin？描述一下编写loader或plugin的思路？



### webpack的热更新是如何做到的？说明其原理？



### 如何利用webpack来优化前端性能？





### 参考文章
 * [关于 webpack 的面试题有哪些？](https://www.zhihu.com/question/266788138/answer/314450633)
 * [前端面试之webpack面试常见问题](https://segmentfault.com/a/1190000014148611)