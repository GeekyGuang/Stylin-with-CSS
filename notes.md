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
> 类的的是为了标识一组具有相同特征的元素，

- 属性选择符
```css
/* 选择有title属性的元素 */
img[title] {border: 1px solid red;}

/* 选择制定属性值的元素 */
img[title="red flower"] {border: 1px solid red;} /*属性值的引号可省略*/
```

- 伪类
> 在某些事件发生时, 改变某些元素的样式，比如用户鼠标悬停在一个链接上。就要靠伪类来实现.
```css
/* 1. UI(user interface用户界面)伪类
*/

a:link {color: black;}  /* 等待被点击 */
a:visited {color: gray;} /* 鼠标点击过了 */
a:hover {text-decoration: none;} /* 鼠标悬浮 , 可以用在其他元素上 */ 
a:active {color:red;} /* 鼠标正在点击的时候 */

e:focus {border: 1px solid red;} /* 获取焦点时 e指任何元素 */

e:target {background: #eee;}  /* e是页面中被a标签href指定的元素 */
#blog:target {background: #eee;} /* <a href="#blog">Link</a> 当点击a标签时, #blog背景变成灰色 */


/* 2. 结构化伪类
  代表一组同胞元素中的第n个元素，
*/

ol.results li:first-child {color: red;}
ol.results li:last-child {color: red;}
li:nth-child(2) {color: red;}
```

- 伪元素
> 文档中若有实无的元素
```css
p::first-letter {font-size:300%}
p::first-line {font-variant:small-caps;}

/* 在元素前后添加内容 */
p.age::before {content:"Age: ";}  
p.age::after {content:" years.";}

/* :after会在元素内容——而不是元素后面插入一个伪元素。*/

```

- 继承，层叠
> CSS有些属性可以继承(文本属性)，有些不能继承(border)

- css属性值
> em 是相对字母M的宽度
> ex 是相对字母x的高度
> rgb: red green blue
> #ff0088 -> #f08 
> rgb(0, 255, 0)
> %r, g%, b% -> 100%, 0%, 90%
> HSL(0, 0%, 0%) 色相，饱和度，亮度


- 定位
> 要掌握CSS技术，核心就是要掌握元素定位
> 可见的页面版式主要由三个属性控制：position属性、display属性和float属性。
```css
/* 上右下左 */
{margin-top: 5px; margin-right: 10px; margin-bottom: 12px; margin-left: 8px;}
/*如果哪个值没有写， 那就使用对边的值。*/
{margin: 5px 10px 12px}  
{margin: 5px 10px }  /*对边相同*/
{margin: 5px} /*四边相同*/

/* 三种粒度 */
{border: 4px solid red;} /* 先给4条边设置相同的样式 */ 
{border-left-width: 1px;} /* 修改左边框宽度 */ 
{border-right: none;} /* 移除右边框 */

/******************************** 
               border
 ********************************/

/* 可上右下左四边分别指定 */
{border-width: thin;}  /* thin, medium, thick */
{border-style: none;} /* none, hidden, dotted, dashed...*/
{border-color: #fff;}
 

{border: solid red;} /* 不指定宽度，则为medium, 3px(google chrome) */

/*  默认情况下，边框的三个相关属性的值分别为 
border-width: medium; 默认 3px
border-style: none; 
border-color: black;
*/

{border-width: 4px 1px 1px 4px;}
{border-width: thin thick medium thin;} 
{border-style: dashed solid;}

/******************************** 
      padding & margin
 ********************************/

 {padding: 10px;} /* 内容的宽度没变，但是盒子的宽度增加了 */

 * {margin:0; padding:0;} /* 去掉默认样式 */

 /* 垂直margin会叠加
    一个margin-top是50， 一个margin-bottom是30， 则两个盒子间距是50
    水平margin不叠加
*/
{margin:.75em 30px;}  /* 上下单位用em, 左右单位用px */

```

- 盒子的宽度
> 如果没有指定width，则默认为auto
> 没有（就是没有设置width的）宽度的元素始终会扩展到填满其父元素的宽度为止。添加水平border、padding和margin，会导致内容宽度减少，减少量等于水平边框、内边距和外边距的和。
> 为设定了宽度的盒子添加边框、内边距和外边距，会导致盒子扩展得更宽。 
> 实际上，盒子的width属性设定的只是盒子内容区的宽度，而非盒子要占据的水平宽度。
> 如果设置了width, 缩小浏览器窗体宽度也不会跟着改变
```css
{box-sizing: content-box;}  /* 默认值，width和height为文本内容 */
{box-sizing: border-box;} /* width和height为文本内容 + padding + border, 注意不包含margin*/
```

- float和clear
> float和clear的作用：1. 文字环绕图片 2. 分栏布局
> float只能左右浮动,并不会上下浮动！！！
> 浮动之后,后面的元素不再认为它在文档流中, 但会绕过其内容
> 浮动非图片元素时, 必须指定宽度
> 分栏布局：将每一栏元素都设为浮动
> 浮动之后，浮动的元素不再被父元素包围
```css
/* 让父元素包围浮动元素的方法 */
/* 1. 父元素添加 overflow: hidden;
*/
section {overflow: hidden;}

/* 2. 父元素添加 float且width 100%
      父元素后面的元素clear
*/
section {float: left; width: 100%;}
img {float: left}
footer {clear: left;}

/* 3. 在包含元素最后添加子元素作为清除元素 */
/* 3.1 最后添加一个div，clear */
.clear_me {clear: left;}

/* 3.2 给父元素添加clearfix类, 添加after伪元素 */
.clearfix::after {
   content: ".";
   display: block;
   height: 0;
   visibility: hidden;
   clear: both;
}

/* content也可以为空 */
.clearfix::after {
   content: "";
   display: block;
   clear: both;
}
```

> clear 是将指定元素移动到前面的浮动元素的下方，不用管指定元素与浮动元素是否是同一级

- :before/after与::before/after的区别
> 前者是CSS2标准，后者是CSS3标准，两者等效
> A::after, A是after的父元素


- 定位
> CSS布局的核心是position属性, 对元素盒子应用这个属性，可以相对于它在常规文档流中的位置重新定位。position属性有 4 个值：static、relative、absolute、fixed，默认值为 static。
```css
/* relative 相对在文档中的原始位置定位，不脱离文档流
*/
{position:relative; top:25px; left:30px;}

/* absolute 绝对定位脱离文档流，相对上下文定位，默认body，会随页面滚动而移动
   绝对定位元素相对于最近的非 static祖先元素定位。
   当这样的祖先元素不存在时，则相对于ICB（inital container block, 初始包含块）
*/
{position:absolute; top:25px; left:30px;}

/* fixed 固定定位和绝对定位类似，定位上下文是视口，不会随页面滚动而移动
*/
{position:fixed; top:25px; left:30px;}

```


- display
```css
/*默认 为 block*/ 
p {display: inline;} 
/*默认 为 inline*/ 
a {display: block;}

/* 把元素的display设定为none，该元素及所有包含在其中的元素，都不会在页面中显示。它们原先占据的所有空间也都会被“回收”，就好像相关的标记根本不存在一样。
*/ 
{display: none;}

/* 只是隐藏元素，但占据的空间仍然保留*/
{visibility: hidden;} /* 默认是visible */

```

- 背景
```css
/* color */
e {
   background-color: #fff;  /* 背景色 */
   color:red;  /* 前景色：文本内容 和 border */
   border:4px solid;
}

/* image */
e {
   background-image:url(images/bg.png);  /* 默认平铺 repeat*/
}

e {
   background-repeat:repeat-x;
   /* 默认是repeat
      还有：
      repeat-x
      repeat-y
      no-repeat
      round 自动调整图片大小以显示完整图片
      space 填充空白以显示完整图片
   */
}

/* background-position
   top left bottom right center 两两组合
*/

{background-position: left center;}  /* 左边居中 */
{background-position: 10% 50%;}  /* 水平 垂直 */
/* 在使用关键字和百分比值的情况下，设定的值同时应用于元素和图片。换句话说，如果设定
   33% 33%，则图片水平33%的位置与元素水平33%的位置对齐。垂直方面也一样。
*/

{background-position: -10px -20px;} /* 图片左上角与元素左上角距离 */


/* background-size
*/
{background-size: 100px 50px;}  /* 固定大小 */
{background-size: 50%;} /* 宽度50%， 高auto */
{background-size: 20% 30%;} /* 宽 高 */
{background-size: cover;} /* 填充 保持宽高比 */
{background-size: contain;} /* 缩放图片，使其与元素等高，保持宽高比 */


/* background-attachment
*/
{background-attachment: fixed;} /* 默认为scroll，设为fixed使背景不会随元素滚动而滚动 */


/* 简写 
*/
{background: url(images/aa.jpg) center #fff no-repeat contain fixed;}


/* 多层背景
   先列出的图片显示在上方(前景)
   背景色在最后
*/

{
background: 
url(images/turq_spiral.png) 30px -10px no-repeat, 
url(images/pink_spiral.png) 145px 0px no-repeat, 
url(images/gray_spiral.png) 140px -30px no-repeat, #ffbd75;
}

```

- 背景渐变
> 注意：书上的与实际的不符，以mdn为准
```css
/* 默认从上到下 */
.gradient1 {
      background:linear-gradient(#e86a43, #fff);
}

/* 从左到右 */
.gradient2 {
      background:linear-gradient(to right, #64d1dd, #fff);
}

/* 左上到右下 */
.gradient3 {
      background:linear-gradient(135deg, #e86a43, #fff);
}


/* 设置渐变点位置
*/
.gradient1 {
      background:linear-gradient(#64d1dd, #fff 50%, #64d1dd);
}
.gradient2 {
      background:linear-gradient(#e86a43, #fff 50%, #e86a43 80%);
}
.gradient3 {
      background:linear-gradient(#64d1dd, #fff 25%, #64d1dd, #fff 75%, #64d1dd);
}
.gradient4 {
      background:linear-gradient(#e86a43, #fff 25%, #64d1dd 25%, #64d1dd 75%, #fff 75%, #e86a43)
}

/* 放射性渐变
*/
/* 默认，根据元素形状而定 */
.gradient1 {
      background: -webkit-radial-gradient(#fff, #64d1dd, #70aa25);
}

/* 圆形 */
.gradient2 {
      background: -webkit-radial-gradient(circle, #fff, #64d1dd, #e86a43);
}

/* 加入圆心位置 */
.gradient3 {
      background: -webkit-radial-gradient(50px 30px, circle, #fff, #64d1dd, #4947ba);
}


```


