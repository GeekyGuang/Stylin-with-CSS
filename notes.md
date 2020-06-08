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
