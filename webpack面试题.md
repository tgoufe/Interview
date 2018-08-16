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
 * file-loader：把文件输出到一个文件夹中，在代码中通过相对 URL 去引用输出的文件
 * url-loader：和 file-loader 类似，但是能在文件很小的情况下以 base64 的方式把文件内容注入到代码中去
 * source-map-loader：加载额外的 Source Map 文件，以方便断点调试
 * image-loader：加载并且压缩图片文件
 * babel-loader：把 ES6 转换成 ES5
 * css-loader：加载 CSS，支持模块化、压缩、文件导入等特性
 * style-loader：把 CSS 代码注入到 JavaScript 中，通过 DOM 操作去加载 CSS。
 * eslint-loader：通过 ESLint 检查 JavaScript 代码


### 有哪些常见的Plugin？他们是解决什么问题的？
 * define-plugin：定义环境变量
 * commons-chunk-plugin：提取公共代码
 * uglifyjs-webpack-plugin：通过 UglifyES 压缩 ES6 代码


### Loader和Plugin的不同？

##### 不同的作用
 * **Loader**直译为"加载器"。Webpack将一切文件视为模块，但是webpack原生是只能解析js文件，如果想将其他文件也打包的话，就会用到`loader`。
所以Loader的作用是让webpack拥有了加载和解析*非JavaScript文件*的能力。

 * **Plugin**直译为"插件"。Plugin可以扩展webpack的功能，让webpack具有更多的灵活性。
 在 Webpack 运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，在合适的时机通过 Webpack 提供的 API 改变输出结果。
 
##### 不同的用法

 * **Loader**在`module.rules`中配置，也就是说他作为模块的解析规则而存在。
 类型为数组，每一项都是一个`Object`，里面描述了对于什么类型的文件（`test`），使用什么加载(`loader`)和使用的参数（`options`）
 * **Plugin**在`plugins`中单独配置。
 类型为数组，每一项是一个`plugin`的实例，参数都通过构造函数传入。



### 如何提高webpack的构建速度？



### webpack的构建流程是什么?从读取配置到输出文件这个过程尽量说全

Webpack 的运行流程是一个串行的过程，从启动到结束会依次执行以下流程：

 1. 初始化参数：从配置文件和 Shell 语句中读取与合并参数，得出最终的参数；
 2. 开始编译：用上一步得到的参数初始化 Compiler 对象，加载所有配置的插件，执行对象的 run 方法开始执行编译；
 3. 确定入口：根据配置中的 entry 找出所有的入口文件；
 4. 编译模块：从入口文件出发，调用所有配置的 Loader 对模块进行翻译，再找出该模块依赖的模块，再递归本步骤直到所有入口依赖的文件都经过了本步骤的处理；
 5. 完成模块编译：在经过第4步使用 Loader 翻译完所有模块后，得到了每个模块被翻译后的最终内容以及它们之间的依赖关系；
 6. 输出资源：根据入口和模块之间的依赖关系，组装成一个个包含多个模块的 Chunk，再把每个 Chunk 转换成一个单独的文件加入到输出列表，这步是可以修改输出内容的最后机会；
 7. 输出完成：在确定好输出内容后，根据配置确定输出的路径和文件名，把文件内容写入到文件系统。
 
在以上过程中，Webpack 会在特定的时间点广播出特定的事件，插件在监听到感兴趣的事件后会执行特定的逻辑，并且插件可以调用 Webpack 提供的 API 改变 Webpack 的运行结果。


### 是否写过Loader和Plugin？描述一下编写loader或plugin的思路？



### webpack的热更新是如何做到的？说明其原理？



### 如何利用webpack来优化前端性能？





### 参考文章
 * [关于 webpack 的面试题有哪些？](https://www.zhihu.com/question/266788138/answer/314450633)
 * [前端面试之webpack面试常见问题](https://segmentfault.com/a/1190000014148611)