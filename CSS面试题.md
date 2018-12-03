# TGFE面试题整理(beta0.1)

## **CSS部分**

### 1.CSS优先级算法如何计算?
```mardown
   一个行内样式:1000，一个id:100，一个属性选择器/class或者伪类:10，一个元素名，或者伪元素:1
   权重大的会覆盖掉权重小的.
   同权重: 内联样式表（标签内部）> 嵌入样式表（当前文件中）> 外部样式表（外部文件中）。
   属性值后加上!important，那么它的优先级最高。
```
 
### 2.Display:none;和visibility:hidden有什么区别？
```markdown
    - 空间占据:display：none;会让元素从渲染树中消失，渲染的时候不占据任何空间；
              visibility：hidden;不会让元素从渲染树中消失，渲染的时候仍然占据空间。
    - 重绘与回流:display：none;会导致页面重绘与回流，影响前端性能。
              visibility：hidden;不会有这个问题。
    - 子孙元素关联:display：none;是非继承属性，子孙节点消失是由于元素从渲染树中消失造成，通过修改子孙节点的属性无法显示；
                visibility：hidden;是继承属性，子孙节点消失是由于继承了hidden，通过设置visibility：visible，可以让子孙节点显示。
```

### 3.什么是高度塌陷？怎么处理高度塌陷？
```markdown

```

### 4.什么是外边距合并
```markdown
  外边距合并:当两个垂直外边距相遇时，它们将形成一个外边距。
  合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。
```

### 5.如何在页面画一个半圆
```css
    .top {
      width: 100px;/*宽度为高度的2倍*/
      height: 50px;
      border-radius: 50px 50px 0 0;/*圆角半径为高度的值*/
    }
    .right {
      height: 100px;/*高度为宽度的2倍*/
      width: 50px;
      border-radius: 0 50px 50px 0;/*圆角半径为宽度的值*/
    }
    .bottom {
      width: 100px;/*宽度为高度的2倍*/
      height: 50px;
      border-radius: 0 0 50px 50px;/*圆角半径为高度的值*/
    }
    .left {
      width: 50px;
      height: 100px;/*高度为宽度的2倍*/
      border-radius: 50px 0 0 50px;/*圆角半径为宽度的值*/
    }
```

### 6.如何在页面画一个三角形
```css
  #demo {
    width: 0;
    height: 0;
    border-width: 20px;
    border-style: solid;
    border-color: transparent transparent red transparent;
  }
```
**把上、左、右三条边隐藏掉（颜色设为 transparent）,也可以使用canvas、svg、旋转正方形等方法**

### 7.什么是HTML语义化？
```markdown
  - 用正确的标签做正确的事情。
  - html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;
  - 即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的;
  - 搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;
  - 使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。
```

### 8.用过哪些CSS预处理器和后处理器？
```markdown
    -预处理器:Less、Sass、Stylus
    -后处理器：clean-css、Autoprefixer
```
### 9.平时会使用哪些CSS3新的属性
```markdown
    - Selector   //CSS3选择器
    - @Font-face //加载字体样式
    - Word-wrap & Text-overflow //换行和超出显示
    - Text-decoration //文字渲染
    - multi-column layout //多列布局
    - CSS3 border //边框圆角、阴影
    - Gradient & Shadow & Reflect //渐变、阴影、反射
    - CSS3 的盒子模型
    - Transitions & Transforms & Animation //动画
```

### 10.响应式布局的基础是什么？
```markdown
    1. 媒体查询
        媒体查询可以让我们获得当前设备的视口宽度、屏幕比例、设备方向（横向或纵向），
        从而实现根据不同设备来设定不同的CSS样式
    2.em(rem)尺寸单位
    3.其他
        栅格系统、流体布局（flex）、百分比布局等
```

### 11.边框（border）和轮廓（ouline）的区别？
```markdown
    1. 轮廓不像边框那样参与到文档流中。因此，轮廓出现或消失时不会影响文档流，即不会导致文档的重新显示。
    2. 轮廓可能不是矩形。用户代理（浏览器）可以"合并"部分轮廓，从而创建一个连续但非矩形的形状。
    3. 轮廓的属性值只能设置一个关键，如out-width和ouline-style不可以像border那样对于4个边分别设置4个关键字。
    4. 轮廓颜色（outline-color）可以设置"反色"（invert），而border没有。他可以确保无论轮廓后面是什么都是可见的。
```