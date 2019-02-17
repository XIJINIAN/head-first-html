# HTML 从入门到还行

[TOC]

## HTML 介绍

### HTML 入门

#### 什么是 HTML

HTML(HyperText Markup Language) 不是一种编程语言，它是一种标记语言，用于告诉您的浏览器如何构造您访问的网页。它可以像Web开发人员希望的那样复杂或简单。

#### HTML 元素

- 构成

   ![](https://i.loli.net/2019/01/13/5c3ac5988dadb.png)

- 嵌套元素

   ```html
   <p>My cat is <strong>very</strong> grumpy.</p>
   ```

- 块级元素和内联元素

   ```html
   <p>fourth</p><p>fifth</p><p>sixth</p>
   <em>first</em><em>second</em><em>third</em>
   ```

- 空元素

   ```html
   <img src="https://raw.githubusercontent.com/mdn/beginner-html-site/gh-pages/images/firefox-icon.png">
   ```

#### 属性

- 布尔属性

   ```html
   <!-- 有时你会看到没有值的属性，它是合法的。这些属性被称为布尔属性，他们只能有跟它的属性名一样的属性值 -->
   <input type="text" disabled="disabled">
   ↓↑
   <input type="text" disabled>
   ```

- 引号不可省略

   ```html
   <!-- 这样的话，title 就是 “The” 了 -->
   <a href=https://www.mozilla.org/ title=The Mozilla homepage>favorite website</a>
   ```

- 单引号还是双引号？

   顺心意。

#### HTML 简单示例

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>My test page</title>
</head>
<body>
<p>This is my page</p>
</body>
</html>

<!--
<!DOCTYPE html> 声明文档类型。
<html> 元素包裹了整个完整的页面，是一个根元素。
<head> 元素是一个容器，它包含了所有你想包含在 HTML 页面中但不想在 HTML 页面中显示的内容。
<meta charset="utf-8"> 这个元素设置文档使用 utf-8 字符集编码，毫无疑问要使用它，这能避免很多问题。
<title> 设置页面标题，出现在浏览器标签上。
<body> 元素包含了你访问页面时所有显示在页面上的内容，文本，图片，音频，游戏等等。
-->
```

#### 实体引用

```html
<p>In HTML, you define a paragraph using the <p> element.</p>
<p>In HTML, you define a paragraph using the &lt;p&gt; element.</p>
```

- 常用转义字符

  | 原义字符 | 等价字符引用 |
  | -------- | ------------ |
  | <        | `&lt;`       |
  | >        | `&gt;`       |
  | "        | `&quot;`     |
  | '        | `&apos;`     |
  | &        | `&amp;`      |


#### HTML 注释

```html
<p>I'm not inside a comment</p>
<!-- <p>I am!</p> -->
```

### HTML 中的 head

#### head 的作用

之前就说过：`<head>` 元素是一个容器，它包含了所有你想包含在 HTML 页面中但不想在 HTML 页面中显示的内容。

#### 元数据

- 元数据就是 描述数据的数据，在 HTML 中就是指 `<meta>` 元素，如我们在 `<head>` 中添加如下代码：

  ```html
  <head>
    <meta charset="utf-8">
    <title>&lt;title&gt; element</title>
  </head>
  ```

- 许多 `<meta>` 元素包含了 name 和 content 属性——其中 name 属性指定了 meta 元素的类型；而 content 属性说明该元素包含了什么类型的信息，指定了实际的元数据内容。举个例子：

  ```html
  <meta name="author" content="Chris Mills">
  <meta name="description" content="The MDN Learning Area aims to provide
  complete beginners to the Web with all they need to know to get
  started with developing web sites and applications.">
  ```

  这两个 meta 元素看起来意义不大，但是在某些内容管理系统能够自动获取页面信息，然后用于某种目的。譬如 Google、譬如 Facebook。

- 真实的例子

  1. 在 Google 搜索引擎中 `<meta>` 元素的使用

     - 搜索 “MDN Web Docs”，界面是这样子的：

        ![](https://i.loli.net/2019/01/13/5c3b471c68470.png)

     - 原理，Google 提取了 MDN 的 description：

       ```html
       <meta name="description" content="The MDN Web Docs site provides information about Open Web technologies including HTML, CSS, and APIs for both Web sites and progressive web apps. It also has some developer-oriented documentation for Mozilla products, such as Firefox Developer Tools.">
       ```

       PS：在谷歌搜索里，在主页面链接下面，你将看到一些相关子页面 — 这些是站点链接，这些其实是在 [Google's webmaster tools](http://www.google.com/webmasters/tools/) 中配置的，它带来一种可以使你的站点对搜索引擎更友好的方式。

  2. 在 Facebook 上花式链接的运用

     - 在 Facebook 上分享 https://developer.mozilla.org/zh-CN/docs/learn 这个链接是这样子的：

        ![](https://i.loli.net/2019/01/13/5c3b44e999244.png)

     - 原理——MDN 实现了 Facebook 编写的元数据协议：

       ```html
       <meta property="og:title" content="学习 Web 开发">
       <meta property="og:url" content="https://developer.mozilla.org/zh-CN/docs/learn">
       <meta property="og:description" content="MDN 的这部分内容并不能让您从“新手”变成“专家”，但可以让您对 Web 开发从“一窍不通”到“感觉不错”。这样您就有足够能力自行学习 MDN 的其他部分，也足以学习需要基础知识的中级甚至是进阶资源。">
       ```

  3. 这种例子实际上还有很多，比如 Twitter 也拥有自己的类型的专有元数据协议，都大同小异：

     ```html
     <meta name="twitter:title" content="学习 Web 开发">
     <meta name="twitter:url" content="https://developer.mozilla.org/zh-CN/docs/learn">
     <meta name="twitter:description" content="MDN 的这部分内容并不能让您从“新手”变成“专家”，但可以让您对 Web 开发从“一窍不通”到“感觉不错”。这样您就有足够能力自行学习 MDN 的其他部分，也足以学习需要基础知识的中级甚至是进阶资源。">
     ```

#### 增加自定义图标

- 添加常规网站图标的两种方式

  1. 将其保存在与网站的索引页相同的目录中，以 .ico 格式保存（大多数浏览器将支持更通用的格式，如 .gif 或 .png，但使用 ICO 格式将确保它能在如 Internet Explorer 6 一样久远的浏览器显示）

  2. 将以下行添加到 HTML `<head>` 中以引用它

     ```html
     <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
     ```

- 其他

  1. iPad

     ```html
     <!-- third-generation iPad with high-resolution Retina display: -->
     <link rel="apple-touch-icon-precomposed" sizes="144x144" href="https://developer.cdn.mozilla.net/static/img/favicon144.a6e4162070f4.png">
     <!-- iPhone with high-resolution Retina display: -->
     <link rel="apple-touch-icon-precomposed" sizes="114x114" href="https://developer.cdn.mozilla.net/static/img/favicon114.0e9fabd44f85.png">
     <!-- first- and second-generation iPad: -->
     <link rel="apple-touch-icon-precomposed" sizes="72x72" href="https://developer.cdn.mozilla.net/static/img/favicon72.8ff9d87c82a0.png">
     <!-- non-Retina iPhone, iPod Touch, and Android 2.1+ devices: -->
     <link rel="apple-touch-icon-precomposed" href="https://developer.cdn.mozilla.net/static/img/favicon57.a2490b9a2d76.png">
     <!-- basic favicon -->
     <link rel="shortcut icon" href="https://developer.cdn.mozilla.net/static/img/favicon32.e02854fdcf73.png">
     ```

  2. ……

#### 应用 CSS 和 JavaScript

使用 CSS 让网页更加炫酷，使用 JavaScript 让网页有交互功能，这些应用在网页中很常见，它们分别使用 `<link>` 元素以及 `<script>` 元素。

- 使用 `<link>` 元素

  ```html
  <link rel="stylesheet" href="my-css-file.css">
  ```

- 使用 `<script>` 元素

  ```html
  <script src="my-js-file.js"></script>
  ```

#### 为文档设定主语言

如果你的 HTML 文档的语言设置好了，那么你的 HTML 文档就会被搜索引擎更有效地索引（例如，允许它在特定于语言的结果中正确显示），对于那些使用屏幕阅读器的视障人士也很有用（例如，法语和英语中都有 “six” 这个单词，但是发音却完全不同）。

```html
<html lang="en-US">
<p>Japanese example: <span lang="jp">ご飯が熱い。</span>.</p>
```

### HTML 文字基础

#### 最常用的表意元素

- `<h1>` 第一级标题，`<h2>` 第二级标题……`<h6>` 第六级标题，在可用的六个标题级别中，您应该旨在每页使用不超过三个，否则看起来眼花缭乱。如果可能，建议将内容分散在多个页面上。
- `<p>` 段落，`<ul><li></li></ul>` 无序列表，`<ol><li></li></ol>` 有序列表，`<em>` 强调，`<strong>` 非常重要。

这些带语义的表意元素其实并没有什么特殊的，但是很多浏览器在实现的时候就给了它们一个默认的样式，譬如 `<em>` 通常是斜体，`<strong>` 通常是粗体，`<h1>` 总是很大，然而这些都不重要，换言之，我们不应该依赖它们，我们更应该自己写好看的 CSS 文件定义样式。还有最重要的——我们决不能贪图浏览器给这些表意元素的默认样式实现，以至于干出“用 `<strong>` 来给文字加粗”、“用 `<em>` 给文字倾斜效果”这种事，因为表意元素是有语义的。如果你只想要加粗、斜体……这些特效，HTML 提供了一些其他的无语义的元素，它们被称为**表象元素**，不过，它们也不应该用来定义样式。

#### 最常用的表象元素

- `<i>` *斜体*
- `<b>` **粗体**
- `<u>` <u>下划线</u>

事实上，我们不仅不应该依赖带语义标签的样式，甚至也不能依赖表象元素提供的样式，因为，它们的样式都是由各个浏览器厂商实现的，不统一且不够个性化。如果我们真的想定义样式，我们应该使用 CSS。

#### 注意

[在 HTML5 中，`<i>`、`<b>` 之流也被赋予了语义](https://www.w3.org/TR/html52/index.html)： `<i>` 元素代表在普通文本中具有不同语态或语气的一段文本，某种程度上表明一段不同特性的文本，比如一个分类学名称，一个技术术语，一个外语习语，一个音译，一个想法，或者西方文本中的一艘船名……；`<b>` 元素代表侧重实用目的而不带有任何额外重要性也不暗示不同语态或语气的一段文本，比如一段文本摘要中的关键词、一段审查中的产品名称、文本驱动软件中的可执行语句或者一篇文章的导语……

不过这些不是那么重要了，反正你还是要自己写 CSS。

再说说 `<u>` 吧，下划线在 Web 中总是凸显着一种“可点击”的气质，所以这玩意乱用会被骂的，在 HTML5 规范中描述“尽量不要用 `<u>`，总有更好的选择”。如果一定要用下划线，那最好用 CSS 给 `<u>` 定义一个“一看就不是普通超链接”的下划线样式。

### 建立超链接

#### 使用 title 属性添加支持信息（鼠标悬停出现）

```html
<p>I'm creating a link to
  <a href="https://www.mozilla.org/en-US/"
     title="The best place to find more information about Mozilla's
            mission and how to contribute">the Mozilla homepage</a>.
</p>
```

#### 块级链接

你可以将一些内容转换为链接，甚至是块级元素。如果你想要将一个图像转换为链接，你只需把图像放到 `<a></a>` 标签中间。

```html
<a href="https://www.mozilla.org/en-US/">
  <img src="mozilla-image.png" alt="mozilla logo that links to the mozilla homepage">
</a>
```

#### 指向本机的地址（相对链接）

这个就跟使用 Linux 差不多，本目录下直接写“文件名”，子目录下直接写“子目录/文件名”，上一级目录就写“../文件名”，父目录是兄弟目录就写“../兄弟目录/文件名 ”

#### 文档片段

超链接可以链接到 html 文档的特定部分（被称为**文档片段**），而不仅仅是文件的顶部。要做到这一点你必须首先分配一个**`id`属性**的元素到链接。

```html
<h2 id="Mailing_address">Mailing address</h2>
<!-- 其他页面来引用 -->
<p>Want to write us a letter? Use our <a href="contacts.html#Mailing_address">mailing address</a>.</p>
<!-- 同页面引用 -->
<p>The <a href="#Mailing_address">company mailing address</a> can be found at the bottom of this page.</p>
```

#### 电子邮件链接

```html
<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
<a href="mailto:">Send email to nowhere</a>
<a href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&amp;
         subject=The%20subject%20of%20the%20email &amp;
         body=The%20body%20of%20the%20email">
  Send mail
</a>
```

#### 链接的最佳实践

1. 用清晰的链接措辞

2. 尽可能使用相对链接（不然会浪费网络等硬件资源，速度慢）

3. 链接到非 HTML 资源，要留下清晰的指示：

   ```html
   <p><a href="http://www.example.com/large-report.pdf">
     Download the sales report (PDF, 10MB)
   </a></p>
   
   <p><a href="http://www.example.com/video-stream/">
     Watch the video (stream opens in separate tab, HD quality)
   </a></p>
   
   <p><a href="http://www.example.com/car-game">
     Play the car game (requires Flash)
   </a></p>
   
   <!-- 在下载链接时使用下载属性 -->
   <a href="https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=en-US"
      download="firefox-latest-64bit-installer.exe">
     Download Latest Firefox for Windows (64-bit) (English, US)
   </a>
   ```

### 高级文字格式

我们在前面的章节 **HTML 文字基础**中学了一些最最基础的元素，接下来说一些不那么常见但是很有用的元素。

#### 描述列表

```html
<dl>
  <!-- 请注意：一个术语<dt>可以同时有多个描述<dd> -->
  <dt>soliloquy</dt>
  <dd>In drama, where a character speaks to themselves, representing their inner thoughts or
    feelings and in the process relaying them to the audience (but not to other characters.)
  </dd>
  <dt>monologue</dt>
  <dd>In drama, where a character speaks their thoughts out loud to share them with the audience and
    any other characters present.
  </dd>
  <dt>aside</dt>
  <dd>In drama, where a character shares a comment only with the audience for humorous or dramatic
    effect. This is usually a feeling, thought or piece of additional background information.
  </dd>
  <dd>In drama, where a character shares a comment only with the audience for humorous or dramatic
    effect. This is usually a feeling, thought or piece of additional background information.
  </dd>
</dl>
```

#### 引用

- 块引用

  ```html
  <blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
    <p>
      The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or <em>HTML Block 
      Quotation Element</em>) indicates that the enclosed text is an extended quotation.
    </p>
  </blockquote>
  ```

- 行内引用

  ```html
  <p>
    The quote element — <code>&lt;q&gt;</code> — is
    <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">
      intended for short quotations that don't require paragraph breaks.
    </q>
  </p>
  ```

- 引文

  ```html
  <p>According to the
    <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
      <cite>MDN blockquote page</cite>
    </a>:
  </p>
  
  <blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
    <p>
      The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong>
      (or <em>HTML Block Quotation Element</em>) indicates that the enclosed 
      text is an extended quotation.
    </p>
  </blockquote>
  
  <p>The quote element — <code>&lt;q&gt;</code> — is
    <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">
      intended for short quotations that don't require paragraph breaks.
    </q>
    --
    <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">
      <cite>MDN q page</cite>
    </a>.
  </p>
  
  <!-- 
  总结：blockquote 元素要 cite 属性（默认样式是缩进），
       q 元素要 cite 属性(默认的样式是加双引号)，
       cite 元素自带斜体效果。
  -->
  ```

#### 缩略语

- abbr

  ```html
  <p>We use <abbr title="Hypertext Markup Language">HTML</abbr> to structure our web documents.</p>
  
  <p>I think <abbr title="Reverend">Rev.</abbr> Green did it in the kitchen with the chainsaw.</p>
  ```

- ~~acronym(专用于首字母缩略词而不是缩略语)~~

#### 联系方式

- `<address>` 元素是为了标记编写HTML文档的人的联系方式，而不是任何其他的内容。

  ```html
  <address>
    <p>Page written by <a href="../authors/chris-mills/">Chris Mills</a>.</p>
  </address>
  ```

#### 上标和下标

- `sup` 和 `sub`

  ```html
  <p>My birthday is on the 25<sup>th</sup> of May 2001.</p>
  <p>Caffeine's chemical formula is C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>.</p>
  ```

#### 展示计算机代码

- `<code>`：用于标记计算机通用代码。
- `<pre>`：对保留的空格（通常是代码块）——如果您在文本中使用缩进或多余的空白，浏览器将忽略它，您将不会在呈现的页面上看到它。但是，如果您将文本包含在 `<pre></pre>` 标签中，那么空白将会以与你在文本编辑器中看到的相同的方式渲染出来。
- `<var>`：用于标记具体变量名。
- `<kbd>`：用于标记输入电脑的键盘（或其他类型）输入。
- `<samp>`：用于标记计算机程序的输出。

#### 标记时间和日期

- 可能的日期表现方式

  ```html
  20 January 2016
  20th January 2016
  Jan 20 2016
  20/06/16
  06/20/16
  The 20th of next month
  20e Janvier 2016
  2016年1月20日
  And so on
  ```

- 可被机器识别的日期格式

  ```html
  <!-- Standard simple date -->
  <time datetime="2016-01-20">20 January 2016</time>
  <!-- Just year and month -->
  <time datetime="2016-01">January 2016</time>
  <!-- Just month and day -->
  <time datetime="01-20">20 January</time>
  <!-- Just time, hours and minutes -->
  <time datetime="19:30">19:30</time>
  <!-- You can do seconds and milliseconds too! -->
  <time datetime="19:30:01.856">19:30:01.856</time>
  <!-- Date and time -->
  <time datetime="2016-01-20T19:30">7.30pm, 20 January 2016</time>
  <!-- Date and time with timezone offset-->
  <time datetime="2016-01-20T19:30+01:00">7.30pm, 20 January 2016 is 8.30pm in France</time>
  <!-- Calling out a specific week number-->
  <time datetime="2016-W04">The fourth week of 2016</time>
  ```

### 文档与网站架构

#### 结构化 HTML

- 标题：`<header>`
- 导航栏：`<nav>`
- 主要内容：`<main>` 具有代表性的内容段落主题可以使用 `<section>`、`<article>` 和 `<div>` 元素
- 侧栏：`<aside>`；经常嵌套在 `<main>` 中
- 页脚：`<footer>`

#### 没有语义的装饰元素

- `<div>`
- `<span>`

#### 换行与水平分割线

- `<br>`
- `<hr>`

#### [详细标准](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Sections_and_Outlines_of_an_HTML5_document)

### HTML 除错

HTML 可以自由的运行，是因为在 Web 创建之初，它的宗旨就是：允许人们获取他们发布的内容比确保所有语法完全正确更重要。如果当初 Web 在一开始就更加严格的话，也许 Web 就不会像今天这样流行了。

也就是说 HTML 的错误相对来说其实并不好检查，MDN 的推荐是这个网站 [Markup Validation Service](https://validator.w3.org/)，我们平时可以在编辑器中使用一些插件来排查错误。

## 多媒体与嵌入

### HTML 中的图片

#### 图片的标准写法

```html
<img src="dinosaur.jpg"
     alt="The head and torso of a dinosaur skeleton;
              it has a large head with long sharp teeth"
     width="400"
     height="341"
     title="A T-Rex on display in the Manchester University Museum">
```

#### `<img>` 的属性

- `alt` — 如果图片没加载出来，留底的文字；
- `width` — 图片的宽度；
- `height` — 图片的高度；
- `title` — 鼠标悬停在图片上面时，弹出的提示文字（`title` 有很多易访问性问题，用到它的时候较少）。

#### 注意

如果你需要改变图片的尺寸，你应该使用 CSS 而不是 HTML。

#### 使用 `<figure>` 元素

经常的，我们需要给图片配上一段说明文字，大概一些人喜欢用 `<p>` 元素直接给 `<img>` 元素配文，然而从语义上来说，不能说明 `<p>`  和 `<img>` 元素之间的关系，这或许会给视障用户们造成很多阻碍。这种情况下我们可以使用 HTML5 带给我们的 `<figure>` 和 `<figcaption>` 元素。

 `<figure>` 的寓意是用紧凑、易于掌握的方式表达你的意图，而其中的  `<figcaption>` 元素时为主要内容提供重要的补充说明 — 这也就意味着，这两个元素不是 `<img>` 元素的私人保姆，你可以用它们“照顾”一段代码、音视频、方程、表格等等等。

写一个代码示例：

```html
<figure>
  <img src="images/dinosaur.jpg"
       alt="The head and torso of a dinosaur skeleton;
            it has a large head with long sharp teeth"
       width="400"
       height="341">
  <figcaption>A T-Rex on display in the Manchester University Museum.</figcaption>
</figure>
```

#### CSS 背景图片

你也可以使用 CSS 把图片嵌入网站中（JavaScript也行，不过那是另外一个故事了），这个 CSS 属性 `background-image` 和另其他 `background-*` 属性是用来放置背景图片的。比如，为页面中的所有段落设置一个背景图片，你可以这样做：

```css
p {
  background-image: url("images/dinosaur.jpg");
}
```

CSS 背景图片可以更好地控制图片和设置图片的位置，但是这样插入的图片完全没有语义上的意义，它们不能有任何备选文本，也不能被屏幕阅读器识别。总而言之，如果图像对您的内容里有意义，则应使用HTML图像。 如果图像纯粹是装饰，则应使用CSS背景图片。

### 视频和音频内容

#### `<video>` 元素

- 一个简单的例子

  ```html
  <video src="rabbit320.webm" controls>
    <p>
      Your browser doesn't support HTML5 video.
      Here is a <a href="rabbit320.webm">link to the video</a> instead.
    </p>
  </video>
  ```

- 属性解读

  1. `src` — 文件的位置；
  2. `controls` — 用户必须能够控制视频和音频的回放功能，且这些媒体应该包括开始和停止，以及调整音量的功能；
  3. `p` — 当浏览器不支持 `<video>` 元素的时候，它将会显示出来。

- 多格式支持

  视频和音频都有不同的格式，如下：

  - WebM 容器通常包括了 Ogg Vorbis 音频和 VP8/VP9 视频。主要在 FireFox 和 Chrome 当中支持。
  - MP4 容器通常包括 AAC 以及 MP3 音频和 H.264 视频。主要在 Internet Explorer 和 Safari 当中支持。
  - 老式的 Ogg 容器往往支持 Ogg Vorbis  音频和 Ogg Theora 视频。主要在 Firefox 和 Chrome 当中支持，不过这个容器已经被更强大的 WebM 容器所取代。

  浏览器并不全支持相同的 codecs（解码音视频用的），所以你得使用几个不同格式的文件来兼容不同的浏览器。如果你使用的格式都得不到浏览器的支持，那么媒体文件将不会播放。

  解决办法如下：

  ```html
  <video controls>
    <source src="rabbit320.mp4" type="video/mp4">
    <source src="rabbit320.webm" type="video/webm">
    <p>
      Your browser doesn't support HTML5 video. Here is a 
      <a href="rabbit320.mp4">link to the video</a> instead.
    </p>
  </video>
  ```

  在这个例子当中，浏览器将会检查 `<source>` 标签，并且播放第一个与其自身 codec 相匹配的媒体。你的视频应当包括 WebM 和 MP4 两种格式，这两种在目前已经足够支持大多数平台和浏览器。每个 `<source>` 标签页含有一个 `type`属性，这个属性是可选的，但是建议你添加上这个属性 — 它包含了视频文件的 MIME types ，同时浏览器也会通过检查这个属性来迅速的跳过那些不支持的格式。如果你没有添加 type 属性，浏览器会尝试加载每一个文件，直到找到一个能正确播放的格式，这样会消耗掉大量的时间和资源。

- 其他属性解读

  ```html
  <video controls width="400" height="400"
         autoplay loop muted
         poster="poster.png">
    <source src="rabbit320.mp4" type="video/mp4">
    <source src="rabbit320.webm" type="video/webm">
    <p>
      Your browser doesn't support HTML5 video. Here is a 
      <a href="rabbit320.mp4">link to the video</a> instead.
    </p>
  </video>
  ```

  - `width`、`height` — 你可以用属性控制视频的尺寸，也可以用 CSS 来控制视频尺寸。无论使用哪种方式，视频都会保持它原始的长宽比 — 也叫做纵横比。如果你设置的尺寸没有保持视频原始长宽比，那么视频边框将会拉伸，而未被视频内容填充的部分，将会显示默认的背景颜色；
  - `autoplay` — 是否自动播放；
  - `loop` — 是否循环；
  - `muted` — 静音；
  - `poster` — 封面；
  - `preload` — 缓冲，有三个值：`none`（不缓冲）、`auto`（页面加载后缓冲）、`metadata`（仅缓冲文件的元数据）。

#### `<audio>` 元素

- 一个简单的例子

  ```html
  <audio controls>
    <source src="viper.mp3" type="audio/mp3">
    <source src="viper.ogg" type="audio/ogg">
    <p>
      Your browser doesn't support HTML5 audio. 
      Here is a <a href="viper.mp3">link to the audio</a> instead.
    </p>
  </audio>
  ```

  `<audio>` 标签与 `<video>` 标签的使用方式几乎完全相同，区别在于它没有视觉部件，因此它不支持 `width/height` 属性，也不支持 `poster` 属性。

#### 显示字幕

WebVTT 是一个格式，用来编写文本文件，这个文本文件包含了众多的字符串，这些字符串会带有一些元数据，它们可以用来描述这个字符串将会在视频中显示的时间，甚至可以用来描述这些字符串的样式以及定位信息。这些字符串叫做 **cues** ，你可以根据不同的需求来显示不同的样式最常见的如下：

- subtitle

  通过添加翻译字幕，来帮助那些听不懂外国语言的人们理解音频当中的内容。

- captions

  同步翻译对白，或是描述一些有重要信息的声音，来帮助那些不能听音频的人们理解音频中的内容。

- timed descriptions

  将文字转换为音频，用于服务那些有视觉障碍的人。

让其与 HTML 媒体一起显示，你需要做如下工作：

1. 以 .vtt 后缀名保存文件。

2. 用 `<track>` 标签链接 .vtt 文件， `<track>` 标签需放在 `<audio>` 或 `<video> 标签当中`，同时需要放在所有 `<source>` 标签之后。使用 `kind` 属性来指明是哪一种类型，如 subtitles 、 captions 、 descriptions。然后，使用 `srclang` 来告诉浏览器你是用什么语言来编写的 subtitles。

   ```html
   <video controls>
     <source src="example.mp4" type="video/mp4">
     <source src="example.webm" type="video/webm">
     <track kind="subtitles" src="subtitles_en.vtt" srclang="en">
   </video>
   ```

3. [更多细节](https://developer.mozilla.org/zh-CN/docs/Web/Apps/Fundamentals/Audio_and_video_delivery/Adding_captions_and_subtitles_to_HTML5_video)

### 其他嵌入技术

#### `<iframe>` 元素

这个元素就是一个网页嵌入另一个网页的内容时使用的

- 一个 YouTube 的例子

  ```html
  <iframe width="560" height="315" 
          src="https://www.youtube.com/embed/xQxThJHJclU"
          frameborder="0"
          allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen>
  </iframe>
  ```

- 属性

  - `allowfullscreen`

    如果设置，`<iframe>` 则可以通过全屏 API 设置为全屏模式；

  - `frameborder`

    如果设置为“1”，则会告诉浏览器在此框架和其他框架之间绘制边框，这是默认行为。设置为“0”是删除边框，不推荐这样设置，因为在 CSS 中可以更好地实现相同的效果 — `border: none;`；

  - `src`

    该属性指向要嵌入本文档资源的 URL 路径；

  - `width` 和 `height`

    这些属性指定您想要的 iframe 的宽度和高度；

  - 备选内容

    与 `video` 等其他类似元素相同，您可以在 `<iframe></iframe>` 标签之间包含备选内容，如果浏览器不支持 `<iframe>`，将会显示备选内容。当然现在您几乎不可能遇到任何不支持 `<iframe>` 的浏览器；

  - `sandbox`

    我们应该**只**给嵌入式内容**所需的权限** — 允许包含在其里的代码以适当的方式执行或者用于测试，但不能对其他代码库（意外或恶意）造成任何损害。默认情况下，您应该使用没有参数的 `sandbox` 属性来强制执行所有可用的限制。如果绝对需要，您可以逐个添加权限（`sandbox="xxx"`）— 其中重要的一点是，你*永远不*应该同时添加 `allow-scripts` 和 `allow-same-origin` 到你的 `sandbox` 属性中，因为这样嵌入式内容可以绕过阻止站点执行脚本的同源安全策略，并使用 JavaScript 完全关闭沙盒。

  #### 配置 CSP 指令

  - `X-Frame-Options` 

    HTTP 响应头是用来给浏览器指示允许一个页面可否在 `<frame>`，`<iframe>` 或者 `<object>` 中展现的标记。网站可以使用此功能，来确保自己网站的内容没有被嵌到别的网站中，从而避免了点击劫持 （clickjacking）的攻击。

    `X-Frame-Options` 有三个值：

    - `DENY`

      表示该页面不允许在 frame 中展示，即便是在相同域名的页面中嵌套也不允许。

    - `SAMEORIGIN`

      表示该页面可以在相同域名页面的 frame 中展示。

    - `ALLOW-FROM uri`

      表示该页面可以在指定来源的 frame 中展示。

  - 想要配置 CSP 就要在对应的服务器中进行配置

    - 配置 Apache 在所有页面上发送 X-Frame-Options 响应头，需要把下面这行添加到 'site' 的配置中

      ```xml
      Header always append X-Frame-Options SAMEORIGIN
      ```

    - 配置 nginx 发送 `X-Frame-Options` 响应头，把下面这行添加到 'http', 'server' 或者 'location' 的配置中

      ```xml
      add_header X-Frame-Options SAMEORIGIN;
      ```

    - …

#### `<embed>` 和 `<object>`

`<embed>`和 `<object>` 元素的功能不同于`<iframe>` — 这些元素是用来嵌入多种类型的外部内容的通用嵌入工具，其中包括像 Java 小程序和 Flash，PDF（可在浏览器中显示为一个 PDF 插件）这样的插件技术（插件是一种对浏览器原生无法读取的内容提供访问权限的软件），甚至像视频，SVG 和图像的内容。

然而，这些都是过去式了，HTML5 原生的功能就很强大，`<embed>`和 `<object>` 元素再见吧，请再也不要使用。

### 在网页中添加矢量图片

#### 什么是矢量图

在网上，你会和两种类型的图片打交道 — 位图和矢量图：位图使用像素网格来定义，矢量图使用算法来定义。

#### 什么是 SVG

SVG 是用于描述矢量图像的 XML 语言。

#### SVG 的优点

- 矢量图像中的文本仍然可访问（这也有利于 SEO）。
- SVG 可以很好地适应样式/脚本，因为图像的每个组件都是可以通过 CSS 或 JavaScript 编写样式的元素。

#### SVG 的缺点

- SVG 非常容易变得复杂，这意味着文件大小会增加；复杂的 SVG 也会在浏览器中占用很长的处理时间。
- SVG 可能比栅格图像更难创建，具体取决于您尝试创建哪种图像。
- 旧版浏览器不支持SVG，因此如果您需要在网站上支持旧版本的 IE，则可能不适合（SVG 从 IE9 开始得到支持）。

#### 将 SVG 添加到页面

1. 快捷方式：`<img>`

   ```html
   <img src="equilateral.svg"
        alt="triangle with all three sides equal"
        height="87px"
        width="100px"/>
   ```

   - 优点

     - 快速，熟悉的图像语法与 `alt` 属性中提供的内置文本等效。
     - 可以通过在 `<a>` 元素嵌套 `<img>`，使图像轻松地成为超链接。

   - 缺点

     - 无法使用 JavaScript 操作图像。
     - 如果要使用 CSS 控制 SVG 内容，则必须在 SVG 代码中包含内联 CSS 样式（从 SVG 文件调用的外部样式表不起作用）。
     - 不能用 CSS 伪类来重设图像样式（如`:focus`）。

   - 处理 HTML 引入 SVG 时的兼容问题

     ```html
     <img src="equilateral.png" alt="triangle with equal sides" srcset="equilateral.svg">
     ```

     在这种情况下，仅支持 SVG 的浏览器会加载 SVG，较旧的浏览器将加载 PNG。

   - 处理 CSS 引入 SVG 背景图片时的兼容问题

     ```css
     background: url("fallback.png") no-repeat center;
     background-image: url("image.svg");
     background-size: contain;
     ```

     像上面描述的 `<img>` 方法一样，使用 CSS 背景图像插入 SVG 意味着它不能被 JavaScript 操作，并且也受到相同的 CSS 限制。

2. 直接在 HTML 中引入 SVG 代码

   - 一个极其简单的示例

     ```html
     <svg width="300" height="200">
       <rect width="100%" height="100%" fill="green"/>
     </svg>
     ```

   - 优点

     - 将 SVG 内联减少 HTTP 请求，可以减少加载时间。
     - 您可以为 SVG 元素分配 `class` 和 `id`，并使用 HTML 文档中的 CSS 样式规则，内联 SVG 是唯一可以让您在 SVG 图像上使用 CSS 交互（如`:focus`）和 CSS 动画的方法。实际上，您可以使用任何 [SVG外观属性](https://developer.mozilla.org/zh-CN/docs/Web/SVG/Attribute#Presentation_attributes) 作为 CSS 属性。
     - 您可以通过将 SVG 标记包在 `<a>` 元素中，使其成为超链接。

   - 缺点

     - 这种方法只适用于在一个地方使用的 SVG，多次使用会导致资源密集型维护。
     - 额外的 SVG 代码会增加 HTML 文件的大小。
     - 浏览器不能像缓存普通图片一样缓存内联 SVG。
     - 您可能会在 `<foreignObject>` 元素中包含回退，但支持 SVG 的浏览器仍然会下载任何后备图像。你需要考虑仅仅为支持过时的浏览器，而增加额外开销是否真的值得。

3. 使用 `<iframe>` 嵌入 SVG

   - 快速回顾

     ```html
     <iframe src="triangle.svg" width="500" height="500" sandbox>
       <img src="triangle.png" alt="Triangle with three unequal sides"/>
     </iframe>
     ```

   - 缺点

     - 如你所知，`iframe` 有一个回退机制，如果浏览器不支持 `iframe`，则只会显示回退。
     - 此外，除非 SVG 和您当前的网页具有相同的 [origin](https://developer.mozilla.org/zh-CN/docs/Glossary/%E6%BA%90)（只有当协议，域名和端口都匹配时，才认为两个对象具有相同的源），否则你不能在主页面上使用 JavaScript 来操纵 SVG。

### 响应式图片

#### 强制采用真实视图

有些手机浏览器会提供不真实的视图宽度，然后加载比浏览器真实视图的宽度大的宽度的网页，然后再缩小加载的页面，这样的做法对响应式图片或其他设计，没有任何帮助。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
→ <meta name="viewport" content="width=device-width">
  <title>Responsive HTML images demo</title>
  <link rel="stylesheet" href="main.css">
</head>
```

#### 分辨率切换

1. 不同的图像显示尺寸，不同的分辨率

   ```html
   <img srcset="elva-fairy-320w.jpg 320w,
                elva-fairy-480w.jpg 480w,
                elva-fairy-800w.jpg 800w"
        sizes="(max-width: 320px) 280px,
               (max-width: 480px) 440px,
               800px"
        src="elva-fairy-800w.jpg"
        alt="Elva dressed as a fairy">
   ```

   `srcset` 定义了我们允许浏览器选择的图像集，以及每个图像的大小（`set` 在这里是集合的意思）；

   `sizes` 定义了一组媒体条件（例如屏幕宽度），并且指明当某些媒体条件为真时，什么样的图像显示尺寸是最佳；

   `src` 是备胎。

   有了这些属性，浏览器会：

   ① 查看设备宽度；

   ② 检查 `sizes` 列表中哪个媒体条件是第一个为真；

   ③ 查看给予该媒体查询的槽大小；

   ④ 加载 `srcset` 列表中引用的最接近所选的槽大小的图像。

2. 相同的图像显示尺寸，不同的分辨率

   ```html
   <img srcset="elva-fairy-320w.jpg,
                elva-fairy-480w.jpg 1.5x,
                elva-fairy-640w.jpg 2x"
        src="elva-fairy-640w.jpg" 
        alt="Elva dressed as a fairy">
   ```

   ```css
   img {
     width: 320px;
   }
   ```

   如果你支持多种分辨率显示，但希望每个人在屏幕上看到的图片的实际尺寸是相同的，你可以让浏览器通过 `srcset` 和 `x` 语法结合。因此，如果访问页面的设备具有标准/低分辨率显示，一个设备像素表示一个 CSS 像素，`elva-fairy-320w.jpg` 会被加载（`1x` 是默认值，所以你不需要写出来）；如果设备有高分辨率，两个或更多的设备像素表示一个CSS 像素，`elva-fairy-640w.jpg` 会被加载。

3. 更改显示的图像以适应不同的图像显示尺寸

   ```html
   <picture>
     <source media="(max-width:799px)" srcset="elva-480w-close-portrait.jpg">
     <source media="(min-width:800px)" srcset="elva-800w.jpg">
     <img src="elva-800w.jpg"
          alt="Chris standing up holding his daughter Elva">
   </picture>
   ```

   这样的代码允许我们在宽屏和窄屏上都能显示合适的图片，**注意**：你应该仅仅当在艺术方向场景下使用 `media` 属性；当你使用 `media` 时，不要在 `sizes` 属性中也提供媒体条件。

#### Why not JavaScript&CSS?

你不能先加载好 `img` 元素后，再用 JavaScript 检测视图的宽度，接着再动态替换最佳尺寸的照片，这样的做法对于响应式图像的理念来说，是背道而驰的。

#### 大胆使用现代图像格式

有很多令人激动的新图像格式（例如 WebP 和 JPEG-2000）可以在有高质量的同时有较低的文件大小。然而，浏览器对其的支持参差不齐。`<picture>` 可以让我们能继续满足老式浏览器的需要。你可以在 `type` 属性中提供 MIME 类型，这样浏览器就能立即拒绝其不支持的文件类型：

```html
<picture>
  <source type="image/svg+xml" srcset="pyramid.svg">
  <source type="image/webp" srcset="pyramid.webp"> 
  <img src="pyramid.png" alt="regular pyramid built from four equilateral triangles">
</picture>
```

注意：

- 不要使用 `media` 属性，除非你需要艺术方向；
- 在 `<source>` 元素中，你只可以引用在 `type` 中声明的文件类型；
- 像之前一样，如果必要，你可以在 `srcset` 和 `sizes` 中使用逗号分割的列表。

## HTML 表格

### HTML 表格基础

#### `<tr>` 和 `<td>`

`<tr>` 就是 “table row”，`<td>` 就是 “table data”，所以一个常见的简单表格是这样写的：

```html
<tr>
  <td>Hi, I'm your first cell.</td>
  <td>I'm your second cell.</td>
  <td>I'm your third cell.</td>
  <td>I'm your fourth cell.</td>
</tr>
```

#### `<th>` 是标题

`<th>` 就是 “table header”，用法和 `<td>` 一样，都是用在 `<tr>` 元素之中。

#### 单元格跨越

通过 colspan（跨列）和 rawspan（跨行）属性进行跨越，举个例子：

```html
<table>
  <tr>
    <th colspan="2">Hippopotamus</th>
  </tr>
  <tr>
    <th rowspan="2">Horse</th>
    <td>Mare</td>
  </tr>
  <tr>
    <td>Stallion</td>
  </tr>
</table>
```

#### 表格样式

1. 笨方法

   ```html
   <table>
     <tr>
       <th>Data 1</th>
       <th style="background-color: yellow">Data 2</th>
     </tr>
     <tr>
       <td>Calcutta</td>
       <td style="background-color: yellow">Orange</td>
     </tr>
     <tr>
       <td>Robots</td>
       <td style="background-color: yellow">Jazz</td>
     </tr>
   </table>
   ```

2. 使用 `colgroup>col` 来快速选择

   ```html
   <table>
     <colgroup>
       <col>
       <col style="background-color: yellow">
     </colgroup>
     <tr>
       <th>Data 1</th>
       <th>Data 2</th>
     </tr>
     <tr>
       <td>Calcutta</td>
       <td>Orange</td>
     </tr>
     <tr>
       <td>Robots</td>
       <td>Jazz</td>
     </tr>
   </table>
   ```

### 表格高级特性和可访问性

#### `<caption>`

给表格增加一个标题

```html
<table>
  <caption>Dinosaurs in the Jurassic period</caption>
  ...
</table>
```

#### 表格中的常用结构

- `<thead>` 放置在头部的位置，因为它通常代表第一行，第一行中往往都是每列的标题，但是不是每种情况都是这样的。如果你使用了 `colgroup>col` 元素，那么 `<thead>` 元素就需要放在它们的下面。
- `<tfoot>` 放置在底部的位置，一般是最后一行，往往是对前面所有行的总结。你也直接紧挨着 `<thead>` 放，不影响浏览器对其位置的渲染。
- `<tbody>` 放置在 `<thead>` 的下面或者是 `<tfoot>` 的下面。

做一个简单的例子：

```html
<table>
  <caption>How I chose to spend my money</caption>
  <thead>
  <tr>
    <th>Purchase</th>
    <th>Location</th>
    <th>Date</th>
    <th>Evaluation</th>
    <th>Cost (€)</th>
  </tr>
  </thead>
  <tfoot>
  <tr>
    <td colspan="4">SUM</td>
    <td>48</td>
  </tr>
  </tfoot>
  <tbody>
  <tr>
    <td>Haircut</td>
    <td>Hairdresser</td>
    <td>12/09</td>
    <td>Great idea</td>
    <td>30</td>
  </tr>
  <tr>
    <td>Lasagna</td>
    <td>Restaurant</td>
    <td>12/09</td>
    <td>Regrets</td>
    <td>18</td>
  </tr>
  </tbody>
</table>
```

#### 嵌套表格

嵌套表格的效果很差，不推荐使用。

```html
<table id="table1">
  <tr>
    <th>title1</th>
    <th>title2</th>
    <th>title3</th>
  </tr>
  <tr>
    <td id="nested">
      <table id="table2">
        <tr>
          <td>cell1</td>
          <td>cell2</td>
          <td>cell3</td>
        </tr>
      </table>
    </td>
    <td>cell2</td>
    <td>cell3</td>
  </tr>
  <tr>
    <td>cell4</td>
    <td>cell5</td>
    <td>cell6</td>
  </tr>
</table>
```

#### 视障用户的表格增强

办法是 — 使用行标题和列标题：

- scope 属性

  ```html
  <thead>
    <tr>
      <th scope="col">Purchase</th>
      <th scope="col">Location</th>
      <th scope="col">Date</th>
      <th scope="col">Evaluation</th>
      <th scope="col">Cost (€)</th>
    </tr>
  </thead>
  ...
  <tr>
    <th scope="row">Haircut</th>
    <td>Hairdresser</td>
    <td>12/09</td>
    <td>Great idea</td>
    <td>30</td>
  </tr>
  
  <!--
  scope 还有两个可选的值：colgroup 和 rowgroup，这些用于位于多个列或行的顶部的标题
  -->
  ```

- id 和标题属性（这种方法实在是太鸡儿繁琐了，一般上面那种就够了，除非特别复杂、重要的表格）

  1. 为每个 `<th>` 元素添加一个 `id`（不能重复）。

  2. 为每个 `<td>` 元素添加一个 `headers` 属性，每个 `headers` 属性需要包含 th 元素的 `id` 。 如果这个单元格是属于一个 th 元素下的，那么就需要包含 th 元素的 id 的值，如果属于多个 th 元素，那么可以用空格分隔这些 id。

     ```html
     <thead>
       <tr>
         <th id="purchase">Purchase</th>
         <th id="location">Location</th>
         <th id="date">Date</th>
         <th id="evaluation">Evaluation</th>
         <th id="cost">Cost (€)</th>
       </tr>
     </thead>
     <tbody>
     <tr>
       <th id="haircut">Haircut</th>
       <td headers="location haircut">Hairdresser</td>
       <td headers="date haircut">12/09</td>
       <td headers="evaluation haircut">Great idea</td>
       <td headers="cost haircut">30</td>
     </tr>
     ...
     </tbody>
     ```

## HTML 表单

### 走进表单

#### 简单表单示例

```html
<form action="/my-handling-form-page" method="post">
  <div>
    <label for="name">Name:</label>
    <input type="text" id="name"/>
  </div>
  <div>
    <label for="mail">E-mail:</label>
    <input type="email" id="mail"/>
  </div>
  <div>
    <label for="msg">Message:</label>
    <textarea id="msg"></textarea>
  </div>
  <div class="button">
    <button type="submit">Send your message</button>
  </div>
</form>
```

#### `<form>`

action 属性就是当你 submit 的时候，将表单内容发送的网址目标；method 属性表示你使用什么 HTTP 协议。

#### `<label>`

这个元素太普通了，没啥特殊的地方，注意一下上面代码中的 for 吧，其关联的是其他组件（如 input、textarea）的 id，显著的好处是，你点击一个 label 的时候，光标直接会聚焦在此 label for 的组件上。

#### `<input>`

对于 input 元素来说，type 是非常重要的属性，因为它定义了 input 的行为方式。

可以用 value 属性来定义它（`input type="text"`）的默认值：`<input type="text" value="your name"/>`

#### `<textarea>`

想定义这个元素的默认值就非常简单了，直接往 `><` 里面塞进去就行。

#### `<button>`

button 元素接受 `submit`、`reset` 或者 `button` 三个值中的一个：

- 单击 `submit` 按钮，发送表单的数据到 form 元素的 `action` 属性所定义的网页；
- 单击 `reset` 按钮，将所有表单小部件重新设置为它们的默认值 — 这用户体验被认为是糟糕的；
- 单击 `button` 按钮，不会发生任何事…这听起来很傻，但是用 JavaScript 构建定制按钮时非常有用。 

#### `<fieldset>`

`fieldset` 元素是一种方便的用于创建具有相同目的的小部件组的方式，出于样式和语义目的。你可以在 `<fieldset>` 开口标签后加上一个 `legend` 元素来给 `fieldset` 标上标签。`legend` 的文本内容正式地描述 `fieldset` 的用途，它是包含在 `<fieldset>` 里的。当阅读下面这个表格时，屏幕阅读器将会读第一个小部件“Fruit juice size small”，“Fruit juice size medium”为第二个，“Fruit juice size large”为第三个。

```html
<form>
  <fieldset>
    <legend>Fruit juice size</legend>
    <p>
      <input type="radio" name="size" id="size_1" value="small">
      <label for="size_1">Small</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_2" value="medium">
      <label for="size_2">Medium</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_3" value="large">
      <label for="size_3">Large</label>
    </p>
  </fieldset>
</form>
```

#### 用于表单的 HTML 结构

举个例子：

```latex
form
  h1
  p
  section
    h2
    fieldset
      legent
      ul>(li>label>input[type=radio])*2
    (p>label+input[type=text])*3
  section
    h2
    p>label+select>option*3
    (p>label+input[type=text])*2
  section
    p>button[type=submit]
form
```

### 原生表单挂件

#### 通用属性

| 属性名称    | 默认值 | 描述                                                         |
| ----------- | ------ | ------------------------------------------------------------ |
| `autofocus` | false  | 这个布尔属性允许您指定当页面加载后某个元素自动具有输入焦点。<br>文档中只有一个与表单相关的元素可以指定这个属性。 |
| `disabled`  | false  | 这个布尔属性表示用户不能与元素交互，此元素可以继承。         |
| `form`      |        | 小部件与之相关联的表单元素，属性值必需是同个文档中某个 form 元素 `id` 属性。<br>理论上，它允许你在 form 元素之外设置一个表单小部件。<br>然而，在实践中，没有任何支持该特性的浏览器。 |
| `name`      |        | 元素的名称 — 这是用于表单数据提交的。                        |
| `value`     |        | 元素的初始值。                                               |

#### 文本输入域

- 文本域通用规范

  - 它们可以被标记为 `readonly`（用户不能修改输入值）甚至是 `disabled`（输入值不会与表单的其余部分一起发送）。
  - 它们可以有一个 `placeholder`，这是文本输入框中出现的文本，用来简略描述输入框的目的。
  - 它们可以被限制在 `size`（框的物理尺寸）和 `maxlength`（可以输入的最大字符数）。
  - 如果浏览器支持的话，他们可以从 `spellcheck`（拼写检查）中获益。

- 单行文本域 `<input>`

  单行文本域只有一个真正的约束：如果您输入带有换行符的文本，浏览器会在发送数据之前删除这些换行符。

  1. E-mail 地址域

     ```html
     <input type="email" id="email" name="email" multiple>
     ```

  2. 密码域

     ```html
     <input type="password" id="pwd" name="pwd">
     ```

  3. 搜索域

     ```html
     <input type="search" id="search" name="search">
     ```

  4. 电话号码域

     ```html
     <input type="tel" id="tel" name="tel">
     ```

  5. URL 域

     ```html
     <input type="url" id="url" name="url">
     ```

- 多行文本域 `<textarea>`

  - 简单示例

    ```html
    <textarea cols="30" rows="10"></textarea>
    ```

    上述是一个典型的 `textarea` 组件，在大多数浏览器中，文本区域在右下角有一个拖放操作，允许用户调整它的大小。这种调整能力可以通过使用 CSS 设置文本区域的 `resize` 性质为 `none` 来关闭。

  - `textarea` 元素常用属性

    | 属性名 | 默认值 | 描述                                                         |
    | ------ | ------ | ------------------------------------------------------------ |
    | `cols` | `20`   | 文本控件的可见宽度，平均字符宽度。                           |
    | `rows` |        | 控制的可见文本行数。                                         |
    | `wrap` | `soft` | 表示控件是如何包装文本的。值：`hard` 或 `soft`（`hard` 在超过宽度时，强制插入换行符） |

  - 注意

    `textarea` 只接受文本内容 — 这意味着将任何 HTML 内容放入 `textarea` 中都呈现为纯文本内容。

#### 下拉内容

- 单选框 `<select>`

  ```html
  <select id="simple" name="simple">
    <option>Banana</option>
    <option selected>Cherry</option>
    <option>Lemon</option>
  </select>
  
  <select id="groups" name="groups">
    <optgroup label="fruits">
      <option>Banana</option>
      <option selected>Cherry</option>
      <option>Lemon</option>
    </optgroup>
    <optgroup label="vegetables">
      <option>Carrot</option>
      <option>Eggplant</option>
      <option>Potato</option>
    </optgroup>
  </select>
  
  <!--
  如果一个 <option> 元素设置了 value 属性，那么当提交表单时该属性的值就会被发送。
  如果忽略了 value 属性，则使用 <option> 元素的内容作为选择框的值。
  -->
  ```

- 多选框

  ```HTML
  <select multiple id="multi" name="multi">
    <option>Banana</option>
    <option>Cherry</option>
    <option>Lemon</option>
  </select>
  ```

- 自动补全输入框

  ```html
  <label for="myFruit">What's your favorite fruit?</label>
  <input type="text" name="myFruit" id="myFruit" list="mySuggestion">
  <datalist id="mySuggestion">
    <option>Apple</option>
    <option>Banana</option>
    <option>Blackberry</option>
    <option>Blueberry</option>
    <option>Lemon</option>
    <option>Lychee</option>
    <option>Peach</option>
    <option>Pear</option>
  </datalist>
  
  <!-- 因为有一些浏览器不支持 datalist，所以下面这种方法也可以试试 -->
  <!-- 原理：支持 datalist 标签的浏览器只会注意到 option，而不支持的则当做 select 列表处理 -->
  <label for="myFruit">What is your favorite fruit? (With fallback)</label>
  <input type="text" id="myFruit" name="fruit" list="fruitList">
  <datalist id="fruitList">
    <label for="suggestion">or pick a fruit</label>
    <select id="suggestion" name="altFruit">
      <option>Apple</option>
      <option>Banana</option>
      <option>Blackberry</option>
      <option>Blueberry</option>
      <option>Lemon</option>
      <option>Lychee</option>
      <option>Peach</option>
      <option>Pear</option>
    </select>
  </datalist>
  ```

#### 可选中项

- 单选框

  ```html
  <input type="radio" checked id="soup" name="meal">
  
  <!-- 当 name 属性一样的时候，只有一个可以被 checked -->
  <fieldset>
    <legend>What is your favorite meal?</legend>
    <ul>
      <li>
        <label for="soup">Soup</label>
        <input type="radio" checked id="soup" name="meal" value="soup">
      </li>
      <li>
        <label for="curry">Curry</label>
        <input type="radio" id="curry" name="meal" value="curry">
      </li>
      <li>
        <label for="pizza">Pizza</label>
        <input type="radio" id="pizza" name="meal" value="pizza">
      </li>
    </ul>
  </fieldset>
  ```

- 复选框

  ```html
  <input type="checkbox" checked id="carrots" name="carrots" value="carrots">
  ```

#### 按钮

之前讲过，重复一遍 — button 元素接受 `submit`、`reset` 或者 `button` 三个值中的一个：

- 单击 `submit` 按钮，发送表单的数据到 form 元素的 `action` 属性所定义的网页；
- 单击 `reset` 按钮，将所有表单小部件重新设置为它们的默认值 — 这用户体验被认为是糟糕的；
- 单击 `button` 按钮，不会发生任何事…这听起来很傻，但是用 JavaScript 构建定制按钮时非常有用。 

#### 高级表单那件选择器部件

- 数字

  ```html
  <input type="number" name="age" id="age" min="1" max="10" step="2">
  ```

- 滑块

  ```html
  <input type="range" name="beans" id="beans" min="0" max="500" step="10">
  ```

- 日期时间选择器

  ```html
  <label for="myDate">When are you available this summer?</label>
  <input type="date" name="myDate" min="2013-06-01" max="2013-08-31" id="myDate">
  ```

- 拾色器

  ```html
  <input type="color" name="color" id="color">
  ```

#### 其他小部件

- 文件选择器

  ```html
  <input type="file" name="file" id="file" accept="image/*" multiple>
  ```

- 隐藏内容

  ```html
  <input type="hidden" id="timestamp" name="timestamp" value="1286705410">
  ```

- 图像按钮

  ```html
  <input type="image" alt="Click me!" src="my-img.png" width="80" height="30">
  ```

- 进度条

  ```html
  <progress max="100" value="75">75/100</progress>
  ```

- 仪表

  ```html
  <meter min="0" max="100" value="75" low="33" high="66" optimum="50">75</meter>
  ```