# TGFE面试题整理(beta0.1)

## **HTML部分**

### 1.`<script>`写在`<head>`和`<body>`中的区别

```markdown
   * HTML 标准<script>不应该出现在<body>中
   * 浏览器有容错设计，所以写在<body>中也不会出错
   * 但是会产生FOUC、重绘等问题
   * <style scoped>这种写法是可以写在body元素中的，但是后来的标准中又删掉了
```

### 2.什么是CSSOM树和DOM树？
```markdown

```

### 3.浏览器是如何解析、渲染页面的？
```markdown

```

### 4.不同浏览器盒模型有什么区别？
```markdown

```
### 5.什么是flexbox？flexbox有哪些属性？
```markdown
     
```

### 6.Doctype是什么? HTML5 为什么只需要写 <!DOCTYPE HTML>？
```markdown
   HTML5 不基于SGML(标准通用标记语言)，因此不需要对DTD进行引用，但是需要Doctype来规范浏览器的行为；
   而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。
```

### 7.什么是渐进增强和优雅降级?
```markdown

```

