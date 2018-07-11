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

```

### 5.如何在页面画一个半圆
```css

```

### 6.如何在页面画一个三角形
```css

```

### 7.什么是HTML语义化？
```markdown

```

### 8.用过哪些CSS预处理器和后处理器？
```markdown
    -预处理器:Less、Sass、Stylus
    -后处理器：clean-css、Autoprefixer
```
### 9.平时会使用哪些CSS3新的属性
```css

```

### 10.响应式布局的基础是什么？
```markdown

```