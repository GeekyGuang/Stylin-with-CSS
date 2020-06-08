- <em> emphasis </em>
- 块级元素盒子会扩展到与父元素同宽。
- 行内元素盒子会“收缩包裹”其内容,并且会尽可能包紧。
- HTML标签每个层次相对于上一层次都缩进 4 个 空格，
- html字符实体 &amp; &ldquo; &rdquo;
- <abbr title="As soon as possible">ASAP</abbr>  // 下划线，鼠标hover显示title
- <strong>absolutely critical</strong> // 加粗
- <em>everyone</em>  // 斜体
- 文档对象模型（Document Object Model， DOM）
- 使用CSS的三种方式
```html
<!-- 1. 行内样式 -->
<p style="font-size: 12px; color: red; font-weight: bold;">By adding inline CSS styling to this paragraph, you override the default styles.</p>

<!-- 2. 嵌入样式 -->
<head>
    <style type="text/css">
      p {color: red;}
    </style>
</head>

<!-- 3. 链接样式 -->
<link rel="stylesheet" type="text/css" href="styles.css" />

<!-- 在样式表中链接其他样式 -->
@import url(css/styles2.css)

<!-- 优先级 -->
行内样式 》 嵌入样式 》 链接样式
```

- 选择器 selector
```css
/* 1. 分组 */
h1, h2, h3 {color: red;}

/* (上下文选择)后代组合选择器: 以空格分隔 */
p em {color: green;}  /* 选择以p元素为祖先的所有em元素. */
article h1 em {color: green;}

/* 子选择符: > 
   标签1 > 标签2
   标签2是标签1第一层子元素，标签1是标签2的父元素
*/
section > a {color: red;}
section > p > a {color: red;}

/* 紧邻同胞选择符 +
   标签1 + 标签2
   标签2是紧跟在标签1后面的第一个兄弟元素
*/
h2 + p {color: red;}


/* 一般同胞选择符 ~
   标签1 ~ 标签2
   标签2是在标签1后面的所有兄弟元素
*/
h2 ~ p {color: red;}   

/* 通用选择符 *
   匹配任何元素
*/
  section * {color: red;}

/* 非子选择符 
   下例：a 不是 section的子元素，而是孙子及后代
*/
section * a {color: red;}

/* 类选择器 .
*/
.specialtext {font-style: italic;} 
p.specialtext {color: red;} 
p.specialtext span {font-weight: bold;}

/* ID选择器 #
*/
#specialtext {font-style: italic;} 
p#specialtext {color: red;} 

```

- 多类选择器
```html
<!-- 以空格分隔多个类名 -->
<p class="one two three">hello world</p>
```
```css
/* 选择同时存在多个类名的元素 */
.one.two.three {font-size: 120%;}
```

- 用于页内导航的ID
```html
<h2 id="bio">hello world</h2>
<a href="#">#占位符,定位到页首</a>  <!-- 返回顶部 -->
<a href="#bio">定位到页内ID</a>

```

- 什么时候使用ID和类
> ID表示的是页面中一个唯一的HTML元素，一个ID只能出现一次。
  给每个顶级区域都添加一个ID，从而得到非常明确的上下文。
> 



