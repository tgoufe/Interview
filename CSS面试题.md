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
    -重绘与回流:display：none;会导致页面重绘与回流，影响前端性能。
              visibility：hidden;不会有这个问题。
    -子孙元素关联:display：none;是非继承属性，子孙节点消失是由于元素从渲染树中消失造成，通过修改子孙节点的属性无法显示；
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