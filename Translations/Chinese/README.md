# 前端工作面试问题

本文包含了一些用于考查候选者的前端面试问题。不建议对单个候选者问及每个问题 (那需要好几个小时)。只要从列表里挑选一些，就能帮助你考查候选者是否具备所需要的技能。

**备注：** 这些问题中很多都是开放性的，可以引发有趣的讨论。这比直接的答案更能体现此人的能力。

## <a name='toc'>目录</a>

  1. [常见问题](#general-questions)
  1. [HTML 相关问题](#html-questions)
  1. [CSS 相关问题](#css-questions)
  1. [JS 相关问题](#js-questions)
  1. [测试相关问题](#testing-questions)
  1. [效能相关问题](#performance-questions)
  1. [网络相关问题](#network-questions)
  1. [代码相关问题](#coding-questions)
  1. [趣味问题](#fun-questions)

## 参与协作

  1. [贡献者](#contributors)
  1. [如何参与贡献](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/CONTRIBUTING.md)
  1. [许可协议](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/LICENSE.md)

#### <a name='general-questions'>常见问题：</a>

* 你在昨天/本周学到了什么？
* 编写代码的哪些方面能够使你兴奋或感兴趣？
* 你最近遇到过什么技术挑战？你是如何解决的？
* 在制作一个网页应用或网站的过程中，你是如何考虑其 UI、安全性、高性能、SEO、可维护性以及技术因素的？
* 请谈谈你喜欢的开发环境。
* 你最熟悉哪一套版本控制系统？
* 你能描述当你制作一个网页的工作流程吗？
* 假若你有 5 个不同的样式文件 (stylesheets), 整合进网站的最好方式是?
* 你能描述渐进增强 (progressive enhancement) 和优雅降级 (graceful degradation) 之间的不同吗?
* 你如何对网站的文件和资源进行优化？
* 浏览器同一时间可以从一个域名下载多少资源？
  * 有什么例外吗？
* 请说出三种减少页面加载时间的方法。(加载时间指感知的时间或者实际加载时间)
* 如果你参与到一个项目中，发现他们使用 Tab 来缩进代码，但是你喜欢空格，你会怎么做？
* 请写一个简单的幻灯效果页面。
* 如果今年你打算熟练掌握一项新技术，那会是什么？
* 请谈谈你对网页标准和标准制定机构重要性的理解。
* 什么是 FOUC (无样式内容闪烁)？你如何来避免 FOUC？
* 请解释什么是 ARIA 和屏幕阅读器 (screenreaders)，以及如何使网站实现无障碍访问 (accessible)。
* 请解释 CSS 动画和 JavaScript 动画的优缺点。
* 什么是跨域资源共享 (CORS)？它用于解决什么问题？

#### <a name='html-questions'>HTML 相关问题：</a>

##### `doctype`(文档类型) 的作用是什么？

`DOCTYPE`是“document type”的缩写。它是 HTML 中用来区分标准模式和[怪异模式](https://quirks.spec.whatwg.org/#history)的声明，用来告知浏览器使用标准模式渲染页面。

从中获得的启发：在页面开始处添加`<!DOCTYPE html>`即可。

##### 浏览器标准模式 (standards mode) 、几乎标准模式（almost standards mode）和怪异模式 (quirks mode) 之间的区别是什么？

暂无

##### HTML 和 XHTML 有什么区别？

暂无

##### 如果页面使用 'application/xhtml+xml' 会有什么问题吗？

暂无

##### 如果网页内容需要支持多语言，你会怎么做？

这个问题有点问得含糊其辞，我认为这是在询问最常见的情况：如何提供包含多种语言内容的页面，并保证页面内容语言的一致性。

当客户端向服务器发送 HTTP 请求时，通常会发送有关语言首选项的信息，比如使用`Accept-Language`请求头。如果替换语言存在，服务器可以利用该信息返回与之相匹配的 HTML 文档。返回的 HTML 文档还应在`<html>`标签中声明`lang`属性，比如`<html lang="en">...</html>`

在后台中，HTML 将包含`i18n`占位符和待以替换的内容，这些按照不同语言，以 YML 或 JSON 格式存储。然后，服务器将动态生成指定语言内容的 HTML 页面。整个过程通常需要借助后台框架实现。

##### 在设计和开发多语言网站时，有哪些问题你必须要考虑？

* 在 HTML 中使用`lang`属性。
* 引导用户切换到自己的母语——让用户能够轻松地切换到自己的国家或语言，而不用麻烦。
* 在图片中展示文本会阻碍网站规模增长——把文本放在图片中展示，仍然是一种非常流行的方式。这样做可以在所有终端上，都能显示出美观的非系统字体。然而，为了翻译图片中的文本，需要为每种语言单独创建对应的图片，这种做法很容易在图片数量不断增长的过程中失控。
* 限制词语或句子的长度——网页内容在使用其他语言表述时，文字长度会发生变化。设计时，需要警惕文字长度溢出布局的问题，最好不要使用受文字长度影响较大的设计。比如标题、标签、按钮的设计，往往很受文字长度影响，这些设计中的文字与正文或评论部分不同，一般不可以自由换行。
* 注意颜色的使用——颜色在不同的语言和文化中，意义和感受是不同的。设计时应该使用恰当的颜色。
* 日期和货币的格式化——日期在不同的国家和地区，会以不同的方式显示。比如美国的日期格式是“May 31, 2012”，而在欧洲部分地区，日期格式是“31 May 2012”。
* 不要使用连接的翻译字符串——不要做类似这样的事情，比如`“今天的日期是”+具体日期`。这样做可能会打乱其他语言的语序。替代方案是，为每种语言编写带变量替换的模版字符串。请看下面两个分别用英语和中文表示的句子：`I will travel on {% date %}`和`{% date %} 我会出发`。可以看到，语言的语法规则不同，变量的位置是不同的。
* 注意语言阅读的方向——在英语中，文字是从左向右阅读的；而在传统日语中，文字是从右向左阅读的。

##### 使用 `data-` 属性的好处是什么？

在 JavaScript 框架变得流行之前，前端开发者经常使用`data-`属性，把额外数据存储在 DOM 自身中。当时没有其他 Hack 手段（比如使用非标准属性或 DOM 上额外属性）。这样做是为了将自定义数据存储到页面或应用中，对此没有其他更适当的属性或元素。

而现在，不鼓励使用`data-`属性。原因之一是，用户可以通过在浏览器中利用检查元素，轻松地修改属性值，借此修改数据。数据模型最好存储在 JavaScript 本身中，并利用框架提供的数据绑定，使之与 DOM 保持更新

##### 如果把 HTML5 看作做一个开放平台，那它的构建模块有哪些？

* 语义 - 提供更准确地描述内容。
* 连接 - 提供新的方式与服务器通信。
* 离线和存储 - 允许网页在本地存储数据并有效地离线运行。
* 多媒体 - 在 Open Web 中，视频和音频被视为一等公民（first-class citizens）。
* 2D/3D 图形和特效 - 提供更多种演示选项。
* 性能和集成 - 提供更快的访问速度和性能更好的计算机硬件。
* 设备访问 - 允许使用各种输入、输出设备。
* 外观 - 可以开发丰富的主题。

##### 请描述 `cookies`、`sessionStorage` 和 `localStorage` 的区别。

上面提到的技术名词，都是在客户端以键值对存储的存储机制，并且只能将值存储为字符串。

|                                                    | `cookie`                                           | `localStorage` | `sessionStorage` |
| -------------------------------------------------- | -------------------------------------------------- | -------------- | ---------------- |
| 由谁初始化                                         | 客户端或服务器，服务器可以使用`Set-Cookie`请求头。 | 客户端         | 客户端           |
| 过期时间                                           | 手动设置                                           | 永不过期       | 当前页面关闭时   |
| 在当前浏览器会话（browser sessions）中是否保持不变 | 取决于是否设置了过期时间                           | 是             | 否               |
| 是否随着每个 HTTP 请求发送给服务器                 | 是，Cookies 会通过`Cookie`请求头，自动发送给服务器 | 否             | 否               |
| 容量（每个域名）                                   | 4kb                                                | 5MB            | 5MB              |
| 访问权限                                           | 任意窗口                                           | 任意窗口       | 当前页面窗口     |

##### 请解释 `<script>`、`<script async>` 和 `<script defer>` 的区别。

* `<script>` - HTML 解析中断，脚本被提取并立即执行。执行结束后，HTML 解析继续。
* `<script async>` - 脚本的提取、执行的过程与 HTML 解析过程并行，脚本执行完毕可能在 HTML 解析完毕之前。当脚本与页面上其他脚本独立时，可以使用`async`，比如用作页面统计分析。
* `<script defer>` - 脚本仅提取过程与 HTML 解析过程并行，脚本的执行将在 HTML 解析完毕后进行。如果有多个含`defer`的脚本，脚本的执行顺序将按照在 document 中出现的位置，从上到下顺序执行。

注意：没有`src`属性的脚本，`async`和`defer`属性会被忽略。

##### 为什么通常推荐将 CSS `<link>` 放置在 `<head></head>` 之间，而将 JS `<script>` 放置在 `</body>` 之前？你知道有哪些例外吗？

**把`<link>`放在`<head>`中**

把`<link>`标签放在`<head></head>`之间是规范要求的内容。此外，这种做法可以让页面逐步呈现，提高了用户体验。将样式表放在文档底部附近，会使许多浏览器（包括 Internet Explorer）不能逐步呈现页面。一些浏览器会阻止渲染，以避免在页面样式发生变化时，重新绘制页面中的元素。这种做法可以防止呈现给用户空白的页面或没有样式的内容。

**把`<script>`标签恰好放在`</body>`之前**

脚本在下载和执行期间会阻止 HTML 解析。把`<script>`标签放在底部，保证 HTML 首先完成解析，将页面尽早呈现给用户。

例外情况是当你的脚本里包含`document.write()`时。但是现在，`document.write()`不推荐使用。同时，将`<script>`标签放在底部，意味着浏览器不能开始下载脚本，直到整个文档（document）被解析。也许，对此比较好的做法是，`<script>`使用`defer`属性，放在`<head>`中。

##### 什么是渐进式渲染 (progressive rendering)？

渐进式渲染是用于提高网页性能（尤其是提高用户感知的加载速度），以尽快呈现页面的技术。

在以前互联网带宽较小的时期，这种技术更为普遍。如今，移动终端的盛行，而移动网络往往不稳定，渐进式渲染在现代前端开发中仍然有用武之地。

一些举例：

* 图片懒加载——页面上的图片不会一次性全部加载。当用户滚动页面到图片部分时，JavaScript 将加载并显示图像。
* 确定显示内容的优先级（分层次渲染）——为了尽快将页面呈现给用户，页面只包含基本的最少量的 CSS、脚本和内容，然后可以使用延迟加载脚本或监听`DOMContentLoaded`/`load`事件加载其他资源和内容。
* 异步加载 HTML 片段——当页面通过后台渲染时，把 HTML 拆分，通过异步请求，分块发送给浏览器。更多相关细节可以在[这里](http://www.ebaytechblog.com/2014/12/08/async-fragments-rediscovering-progressive-html-rendering-with-marko/)找到。

##### 你用过哪些不同的 HTML 模板语言？

有过，比如 Pug （以前叫 Jade）、 ERB、 Slim、 Handlebars、 Jinja、 Liquid 等等。在我看来，这些模版语言大多是相似的，都提供了用于展示数据的内容替换和过滤器的功能。大部分模版引擎都支持自定义过滤器，以展示自定义格式的内容。

#### <a name='css-questions'>CSS 相关问题：</a>

##### CSS 中类 (classes) 和 ID 的区别。

暂无

##### 请问 "resetting" 和 "normalizing" CSS 之间的区别？你会如何选择，为什么？

* **重置（Resetting）**： 重置意味着除去所有的浏览器默认样式。对于页面所有的元素，像`margin`、`padding`、`font-size`这些样式全部置成一样。你将必须重新定义各种元素的样式。
* **标准化（Normalizing）**： 标准化没有去掉所有的默认样式，而是保留了有用的一部分，同时还纠正了一些常见错误。

当需要实现非常个性化的网页设计时，我会选择重置的方式，因为我要写很多自定义的样式以满足设计需求，这时候就不再需要标准化的默认样式了。

##### 请解释浮动 (Floats) 及其工作原理。

浮动（float）是 CSS 定位属性。浮动元素从网页的正常流动中移出，但是保持了部分的流动性，会影响其他元素的定位（比如文字会围绕着浮动元素）。这一点与绝对定位不同，绝对定位的元素完全从文档流中脱离。

CSS 的`clear`属性通过使用`left`、`right`、`both`，让该元素向下移动（清除浮动）到浮动元素下面。

如果父元素只包含浮动元素，那么该父元素的高度将塌缩为 0。我们可以通过清除（clear）从浮动元素后到父元素关闭前之间的浮动来修复这个问题。

有一种 hack 的方法，是自定义一个`.clearfix`类，利用伪元素选择器`::after`清除浮动。[另外还有一些方法](https://css-tricks.com/all-about-floats/#article-header-id-4)，比如添加空的`<div></div>`和设置浮动元素父元素的`overflow`属性。与这些方法不同的是，`clearfix`方法，只需要给父元素添加一个类，定义如下：

```css
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}
```

值得一提的是，把父元素属性设置为`overflow: auto`或`overflow: hidden`，会使其内部的子元素形成块格式化上下文（Block Formatting Context），并且父元素会扩张自己，使其能够包围它的子元素。

##### 描述`z-index`和叠加上下文是如何形成的。

CSS 中的`z-index`属性控制重叠元素的垂直叠加顺序。`z-index`只能影响`position`值不是`static`的元素。

没有定义`z-index`的值时，元素按照它们出现在 DOM 中的顺序堆叠（层级越低，出现位置越靠上）。非静态定位的元素（及其子元素）将始终覆盖静态定位（static）的元素，而不管 HTML 层次结构如何。

层叠上下文是包含一组图层的元素。 在一组层叠上下文中，其子元素的`z-index`值是相对于该父元素而不是 document root 设置的。每个层叠上下文完全独立于它的兄弟元素。如果元素 B 位于元素 A 之上，则即使元素 A 的子元素 C 具有比元素 B 更高的`z-index`值，元素 C 也永远不会在元素 B 之上.

每个层叠上下文是自包含的：当元素的内容发生层叠后，整个该元素将会在父层叠上下文中按顺序进行层叠。少数 CSS 属性会触发一个新的层叠上下文，例如`opacity`小于 1，`filter`不是`none`，`transform`不是`none`。

##### 请描述 BFC(Block Formatting Context) 及其如何工作。

块格式上下文（BFC）是 Web 页面的可视化 CSS 渲染的部分，是块级盒布局发生的区域，也是浮动元素与其他元素交互的区域。

一个 HTML 盒（Box）满足以下任意一条，会创建块格式化上下文：

* `float`的值不是`none`.
* `position`的值不是`static`或`relative`.
* `display`的值是`table-cell`、`table-caption`、`inline-block`、`flex`、或`inline-flex`。
* `overflow`的值不是`visible`。

在 BFC 中，每个盒的左外边缘都与其包含的块的左边缘相接。

两个相邻的块级盒在垂直方向上的边距会发生合并（collapse）。更多内容请参考[边距合并（margin collapsing）](https://www.sitepoint.com/web-foundations/collapsing-margins/)。

##### 列举不同的清除浮动的技巧，并指出它们各自适用的使用场景。

* 空`div`方法：`<div style="clear:both;"></div>`。
* Clearfix 方法：上文使用`.clearfix`类已经提到。
* `overflow: auto`或`overflow: hidden`方法：上文已经提到。

在大型项目中，我会使用 Clearfix 方法，在需要的地方使用`.clearfix`。设置`overflow: hidden`的方法可能使其子元素显示不完整，当子元素的高度大于父元素时。

##### 请解释 CSS sprites，以及你要如何在页面或网站中实现它。

雪碧图是把多张图片整合到一张上的图片。它被运用在众多使用了很多小图标的网站上（Gmail 在使用）。实现方法：

1. 使用生成器将多张图片打包成一张雪碧图，并为其生成合适的 CSS。
1. 每张图片都有相应的 CSS 类，该类定义了`background-image`、`background-position`和`background-size`属性。
1. 使用图片时，将相应的类添加到你的元素中。

好处：

* 减少加载多张图片的 HTTP 请求数（一张雪碧图只需要一个请求）。但是对于 HTTP2 而言，加载多张图片不再是问题。
* 提前加载资源，防止在需要时才在开始下载引发的问题，比如只出现在`:hover`伪类中的图片，不会出现闪烁。

##### 你最喜欢的图片替换方法是什么，你如何选择使用。

暂无

##### 你会如何解决特定浏览器的样式问题？

* 在确定问题原因和有问题的浏览器后，使用单独的样式表，仅供出现问题的浏览器加载。这种方法需要使用服务器端渲染。
* 使用已经处理好此类问题的库，比如 Bootstrap。
* 使用 `autoprefixer` 自动生成 CSS 属性前缀。
* 使用 Reset CSS 或 Normalize.css。

##### 如何为有功能限制的浏览器提供网页？
  ###### 你会使用哪些技术和处理方法？

* 优雅的降级：为现代浏览器构建应用，同时确保它在旧版浏览器中正常运行。
* Progressive enhancement - The practice of building an application for a base level of user experience, but adding functional enhancements when a browser supports it.
* 渐进式增强：构建基于用户体验的应用，但在浏览器支持时添加新增功能。
* 利用 [caniuse.com](https://caniuse.com/) 检查特性支持。
* 使用 `autoprefixer` 自动生成 CSS 属性前缀。
* 使用 [Modernizr](https://modernizr.com/)进行特性检测

##### 有哪些的隐藏内容的方法 (如果同时还要保证屏幕阅读器可用呢)？

这些方法与可访问性（a11y）有关。

* `visibility: hidden`：元素仍然在页面流中，并占用空间。
* `width: 0; height: 0`：使元素不占用屏幕上的任何空间，导致不显示它。
* `position: absolute; left: -99999px`： 将它置于屏幕之外。
* `text-indent: -9999px`：这只适用于`block`元素中的文本。
* Metadata： 例如通过使用 Schema.org，RDF 和 JSON-LD。
* WAI-ARIA：如何增加网页可访问性的 W3C 技术规范。

即使 WAI-ARIA 是理想的解决方案，我也会采用绝对定位方法，因为它具有最少的注意事项，适用于大多数元素，而且使用起来非常简单。

##### 你用过栅格系统 (grid system) 吗？如果使用过，你最喜欢哪种？

我使用 `float`-based 栅格系统，因为它相比 flex、grid 系统，拥有更多浏览器的支持。它已经在 Bootstrap 中使用多年，并且已经被证明是可行的。

##### 你用过媒体查询，或针对移动端的布局/CSS 吗？

是的，一个例子就是根据窗口的尺寸改变导航的样式。

##### 你熟悉 SVG 样式的书写吗？

不好意思，不熟悉。

##### 如何优化网页的打印样式？

暂无

##### 在书写高效 CSS 时会有哪些问题需要考虑？

首先，浏览器从最右边的选择器，即关键选择器（key selector），向左依次匹配。根据关键选择器，浏览器从 DOM 中筛选出元素，然后向上遍历被选元素的父元素，判断是否匹配。选择器匹配语句链越短，浏览器的匹配速度越快。避免使用标签和通用选择器作为关键选择器，因为它们会匹配大量的元素，浏览器必须要进行大量的工作，去判断这些元素的父元素们是否匹配。

[BEM (Block Element Modifier)](https://bem.info/) methodology recommends that everything has a single class, and, where you need hierarchy, that gets baked into the name of the class as well, this naturally makes the selector efficient and easy to override.
[BEM (Block Element Modifier)](https://bem.info/)原则上建议为独立的 CSS 类命名，并且在需要层级关系时，将关系也体现在命名中，这自然会使选择器高效且易于覆盖。

搞清楚哪些 CSS 属性会触发重新布局（reflow）、重绘（repaint）和合成（compositing）。在写样式时，避免触发重新布局的可能。

##### 使用 CSS 预处理器的优缺点有哪些？
  ###### 请描述你曾经使用过的 CSS 预处理器的优缺点。

优点：

* 提高 CSS 可维护性。
* 易于编写嵌套选择器。
* 引入变量，增添主题功能。可以在不同的项目中共享主题文件。
* 通过混合（Mixins）生成重复的 CSS。
* Splitting your code into multiple files. CSS files can be split up too but doing so will require a HTTP request to download each CSS file.
* 将代码分割成多个文件。不进行预处理的 CSS，虽然也可以分割成多个文件，但需要建立多个 HTTP 请求加载这些文件。

缺点：

* 需要预处理工具。
* 重新编译的时间可能会很慢。

喜欢：

* 绝大部分优点上题以及提过。
* Less 用 JavaScript 实现，与 NodeJS 高度结合。

**Dislikes:**

* 我通过`node-sass`使用 Sass，它用 C ++ 编写的 LibSass 绑定。在 Node 版本切换时，我必须经常重新编译。
* Less 中，变量名称以`@`作为前缀，容易与 CSS 关键字混淆，如`@media`、`@import`和`@font-face`。

##### 如果设计中使用了非标准的字体，你该如何去实现？

使用`@font-face`并为不同的`font-weight`定义`font-family`。

##### 请解释浏览器是如何判断元素是否匹配某个 CSS 选择器？

这部分与上面关于编写高效的 CSS 有关。浏览器从最右边的选择器（关键选择器）根据关键选择器，浏览器从 DOM 中筛选出元素，然后向上遍历被选元素的父元素，判断是否匹配。选择器匹配语句链越短，浏览器的匹配速度越快。

例如，对于形如`p span`的选择器，浏览器首先找到所有`<span>`元素，并遍历它的父元素直到根元素以找到`<p>`元素。对于特定的`<span>`，只要找到一个`<p>`，就知道'<span>`已经匹配并停止继续匹配。

##### 请描述伪元素 (pseudo-elements) 及其用途。

CSS 伪元素是添加到选择器的关键字，去选择元素的特定部分。它们可以用于装饰（`:first-line`，`:first-letter`）或将元素添加到标记中（与 content:...组合），而不必修改标记（`:before`，`:after`）。

* `:first-line`和`:first-letter`可以用来修饰文字。
* 上面提到的`.clearfix`方法中，使用`clear: both`来添加不占空间的元素。
* 使用`:before`和`after`展示提示中的三角箭头。鼓励关注点分离，因为三角被视为样式的一部分，而不是真正的 DOM。如果不使用额外的 HTML 元素，只用 CSS 样式绘制三角形是不太可能的。

##### 请解释你对盒模型的理解，以及如何在 CSS 中告诉浏览器使用不同的盒模型来渲染你的布局。

CSS 盒模型描述了以文档树中的元素而生成的矩形框，并根据排版模式进行布局。每个盒子都有一个内容区域（例如文本，图像等）以及周围可选的`padding`、`border`和`margin`区域。

CSS 盒模型负责计算：

* 块级元素占用多少空间。
* 边框是否重叠，边距是否合并。
* 盒子的尺寸。

盒模型有以下规则：

* 块级元素的大小由`width`、`height`、`padding`、`border`和`margin`决定。
* 如果没有指定`height`，则块级元素的高度等于其包含子元素的内容高度加上`padding`（除非有浮动元素，请参阅下文）。
* 如果没有指定`width`，则非浮动块级元素的宽度等于其父元素的宽度减去父元素的`padding`。
* 元素的`height`是由内容的`height`来计算的。
* 元素的`width`是由内容的`width`来计算的。
* 默认情况下，`padding`和`border`不是元素`width`和`height`的组成部分。

##### 请解释 ```* { box-sizing: border-box; }``` 的作用, 并且说明使用它有什么好处？

* 元素默认应用了`box-sizing: content-box`，元素的宽高只会决定内容（content）的大小。
* `box-sizing: border-box`改变计算元素`width`和`height`的方式，`border`和`padding`的大小也将计算在内。
* 元素的`height` = 内容（content）的高度 + 垂直方向的`padding` + 垂直方向`border`的宽度
* 元素的`width` = 内容（content）的宽度 + 水平方向的`padding` + 水平方向`border`的宽度

##### 请罗列出你所知道的 display 属性的全部值

* `none`, `block`, `inline`, `inline-block`, `table`, `table-row`, `table-cell`, `list-item`.

##### 请解释 inline 和 inline-block 的区别？

我把`block`也加入其中，为了获得更好的比较。

|                                 | `block`                                                     | `inline-block`                             | `inline`                                                                                                           |
| ------------------------------- | ----------------------------------------------------------- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| 大小                            | 填充其父容器的宽度。                                        | 取决于内容。                               | 取决于内容。                                                                                                       |
| 定位                            | 从新的一行开始，并且不允许旁边有 HTML 元素（除非是`float`） | 与其他内容一起流动，并允许旁边有其他元素。 | 与其他内容一起流动，并允许旁边有其他元素。                                                                         |
| 能否设置`width`和`height`       | 能                                                          | 能                                         | 不能。 设置会被忽略。                                                                                              |
| 可以使用`vertical-align`对齐    | 不可以                                                      | 可以                                       | 可以                                                                                                               |
| 边距（margin）和填充（padding） | 各个方向都存在                                              | 各个方向都存在                             | 只有水平方向存在。垂直方向会被忽略。 尽管`border`和`padding`在`content`周围，但垂直方向上的空间取决于'line-height' |
| 浮动（float）                   | -                                                           | -                                          | 就像一个`block`元素，可以设置垂直边距和填充。                                                                      |

##### 请解释 relative、fixed、absolute 和 static 元素的区别

经过定位的元素，其`position`属性值必然是`relative`、`absolute`、`fixed`或`sticky`。

* `static`：默认定位属性值。该关键字指定元素使用正常的布局行为，即元素在文档常规流中当前的布局位置。此时 top, right, bottom, left 和 z-index 属性无效。
* `relative`：该关键字下，元素先放置在未添加定位时的位置，再在不改变页面布局的前提下调整元素位置（因此会在此元素未添加定位时所在位置留下空白）。
* `absolute`：不为元素预留空间，通过指定元素相对于最近的非 static 定位祖先元素的偏移，来确定元素位置。绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。
* `fixed`：不为元素预留空间，而是通过指定元素相对于屏幕视口（viewport）的位置来指定元素位置。元素的位置在屏幕滚动时不会改变。打印时，元素会出现在的每页的固定位置。fixed 属性会创建新的层叠上下文。当元素祖先的 transform 属性非 none 时，容器由视口改为该祖先。
* `sticky`：盒位置根据正常流计算(这称为正常流动中的位置)，然后相对于该元素在流中的 flow root（BFC）和 containing block（最近的块级祖先元素）定位。在所有情况下（即便被定位元素为 `table` 时），该元素定位均不对后续元素造成影响。当元素 B 被粘性定位时，后续元素的位置仍按照 B 未定位时的位置来确定。`position: sticky` 对 `table` 元素的效果与 `position: relative` 相同。

##### CSS 中字母 'C' 的意思是叠层 (Cascading)。请问在确定样式的过程中优先级是如何决定的 (请举例)？如何有效使用此系统？

暂无

##### 你在开发或生产环境中使用过哪些 CSS 框架？你觉得应该如何改善他们？

* **Bootstrap**： 更新周期缓慢。Bootstrap 4 已经处于 alpha 版本将近两年了。添加了在页面中广泛使用的微调按钮组件。
* **Semantic UI**：源代码结构使得自定义主题很难理解。非常规主题系统的使用体验很差。外部库的路径需要硬编码（hard code）配置。变量重新赋值没有 Bootstrap 设计得好。
* **Bulma**： 需要很多非语义的类和标记，显得很多余。不向后兼容，以至于升级版本后，会破坏应用的正常运行。

##### 请问你有尝试过 CSS Flexbox 或者 Grid 标准规格吗？

了解。Flexbox 主要用于一维布局，而 Grid 则用于二维布局。

Flexbox 解决了 CSS 中的许多常见问题，例如容器中元素的垂直居中，粘性定位（sticky）的页脚等。Bootstrap 和 Bulma 基于 Flexbox，这是创建布局的推荐方式。我之前曾使用过 Flexbox，但在使用`flex-grow`时遇到了一些浏览器不兼容问题（Safari），我必须使用`inline-blocks`和手动计算百分比宽度，来重写我的代码，这种体验不是很好。

Grid 创建基于栅格的布局，是迄今为止最直观的方法（最好是！），但目前浏览器支持并不广泛。

##### 为什么响应式设计 (responsive design) 和自适应设计 (adaptive design) 不同？

响应式设计和自适应设计都以提高不同设备间的用户体验为目标，根据视窗大小、分辨率、使用环境和控制方式等参数进行优化调整。

响应式设计的适应性原则：网站应该凭借一份代码，在各种设备上都有良好的显示和使用效果。响应式网站通过使用媒体查询，自适应栅格和响应式图片，基于多种因素进行变化，创造出优良的用户体验。就像一个球通过膨胀和收缩，来适应不同大小的篮圈。

自适应设计更像是渐进式增强的现代解释。与响应式设计单一地去适配不同，自适应设计通过检测设备和其他特征，从早已定义好的一系列视窗大小和其他特性中，选出最恰当的功能和布局。与使用一个球去穿过各种的篮筐不同，自适应设计允许使用多个球，然后根据不同的篮筐大小，去选择最合适的一个。

##### 你有兼容 retina 屏幕的经历吗？如果有，在什么地方使用了何种技术？

我倾向于使用更高分辨率的图形（显示尺寸的两倍）来处理视网膜显示。更好的方法是使用媒体查询，像`@media only screen and (min-device-pixel-ratio: 2) { ... }`，然后改变`background-image`。

对于图标类的图形，我会尽可能使用 svg 和图标字体，因为它们在任何分辨率下，都能被渲染得十分清晰。

还有一种方法是，在检查了`window.devicePixelRatio`的值后，利用 JavaScript 将`<img>`的`src`属性修改，用更高分辨率的版本进行替换。

##### 请问为何要使用 `translate()` 而非 *absolute positioning*，或反之的理由？为什么？

`translate()`是`transform`的一个值。改变`transform`或`opacity`不会触发浏览器重新布局（reflow）或重绘（repaint），只会触发复合（compositions）。而改变绝对定位会触发重新布局，进而触发重绘和复合。`transform`使浏览器为元素创建一个 GPU 图层，但改变绝对定位会使用到 CPU。 因此`translate()`更高效，可以缩短平滑动画的绘制时间。

当使用`translate()`时，元素仍然占据其原始空间（有点像`position：relative`），这与改变绝对定位不同。

#### <a name='js-questions'>JS 相关问题：</a>

##### 请解释事件代理 (event delegation)。

事件委托是将事件监听器添加到父元素，而不是每个子元素单独设置事件监听器。当触发子元素时，事件会冒泡到父元素，监听器就会触发。这种技术的好处是：

* 内存占用减少，因为只需要一个父元素的事件处理程序，而不必为每个后代都添加事件处理程序。
* 无需从已删除的元素中解绑处理程序，也无需将处理程序绑定到新元素上。

##### 请解释 JavaScript 中 `this` 是如何工作的。


JS 中的`this`是一个相对复杂的概念，不是简单几句能解释清楚的。粗略地讲，函数的调用方式决定了`this`的值。我阅读了网上很多关于`this`的文章，[Arnav Aggrawal](https://medium.com/@arnav_aggarwal) 写的比较清楚。`this`取值符合以下规则：

1. 在调用函数时使用`new`关键字，函数内的`this`是一个全新的对象。
1. 如果`apply`、`call`或`bind`方法用于调用、创建一个函数，函数内的 this 就是作为参数传入这些方法的对象。
1. 当函数作为对象里的方法被调用时，函数内的`this`是调用该函数的对象。比如当`obj.method()`被调用时，函数内的 this 将绑定到`obj`对象。
1. 如果调用函数不符合上述规则，那么`this`的值指向全局对象（global object）。浏览器环境下`this`的值指向`window`对象，但是在严格模式下(`'use strict'`)，`this`的值为`undefined`。
1. 如果符合上述多个规则，则较高的规则（1 号最高，4 号最低）将决定`this`的值。
1. 如果该函数是 ES2015 中的箭头函数，将忽略上面的所有规则，`this`被设置为它被创建时的上下文。

##### 请解释原型继承 (prototypal inheritance) 的原理。

这是一个非常常见的 JavaScript 问题。所有 JS 对象都有一个`prototype`属性，指向它的原型对象。当试图访问一个对象的属性时，如果没有在该对象上找到，它还会搜寻该对象的原型，以及该对象的原型的原型，依次层层向上搜索，直到找到一个名字匹配的属性或到达原型链的末尾。这种行为是在模拟经典的继承，[但是与其说是继承，不如说是委托（delegation）](https://davidwalsh.name/javascript-objects)。

##### 你怎么看 AMD vs. CommonJS？

它们都是实现模块体系的方式，直到 ES2015 出现之前，JavaScript 一直没有模块体系。CommonJS 是同步的，而 AMD（Asynchronous Module Definition）从全称中可以明显看出是异步的。CommonJS 的设计是为服务器端开发考虑的，而 AMD 支持异步加载模块，更适合浏览器。

我发现 AMD 的语法非常冗长，CommonJS 更接近其他语言 import 声明语句的用法习惯。大多数情况下，我认为 AMD 没有使用的必要，因为如果把所有 JavaScript 都捆绑进一个文件中，将无法得到异步加载的好处。此外，CommonJS 语法上更接近 Node 编写模块的风格，在前后端都使用 JavaScript 开发之间进行切换时，语境的切换开销较小。

我很高兴看到 ES2015 的模块加载方案同时支持同步和异步，我们终于可以只使用一种方案了。虽然它尚未在浏览器和 Node 中完全推出，但是我们可以使用代码转换工具进行转换。

##### 请解释为什么接下来这段代码不是 IIFE (立即调用的函数表达式)：`function foo(){ }();`.
  ###### 要做哪些改动使它变成 IIFE?

IIFE（Immediately Invoked Function Expressions）代表立即执行函数。 JavaScript 解析器将 `function foo(){ }();`解析成`function foo(){ }`和`();`。其中，前者是函数声明；后者（一对括号）是试图调用一个函数，却没有指定名称，因此它会抛出`Uncaught SyntaxError: Unexpected token )`的错误。

修改方法是：再添加一对括号，形式上有两种：`(function foo(){ })()`和`(function foo(){ }())`。以上函数不会暴露到全局作用域，如果不需要在函数内部引用自身，可以省略函数的名称。

你可能会用到 `void` 操作符：`void function foo(){ }();`。但是，这种做法是有问题的。表达式的值是`undefined`，所以如果你的 IIFE 有返回值，不要用这种做法。例如：

```
// Don't add JS syntax to this code block to prevent Prettier from formatting it.
const foo = void function bar() { return 'foo'; }();

console.log(foo); // undefined
```

##### 描述以下变量的区别：`null`，`undefined` 或 `undeclared`？
  ###### 该如何检测它们？

当你没有提前使用`var`、`let`或`const`声明变量，就为一个变量赋值时，该变量是未声明变量（undeclared variables）。未声明变量会脱离当前作用域，成为全局作用域下定义的变量。在严格模式下，给未声明的变量赋值，会抛出`ReferenceError`错误。和使用全局变量一样，使用未声明变量也是非常不好的做法，应当尽可能避免。要检查判断它们，需要将用到它们的代码放在`try`/`catch`语句中。

```js
function foo() {
  x = 1; // 在严格模式下，抛出 ReferenceError 错误
}

foo();
console.log(x); // 1
```

当一个变量已经声明，但没有赋值时，该变量的值是`undefined`。如果一个函数的执行结果被赋值给一个变量，但是这个函数却没有返回任何值，那么该变量的值是`undefined`。要检查它，需要使用严格相等（`===`）；或者使用`typeof`，它会返回`'undefined'`字符串。请注意，不能使用非严格相等（`==`）来检查，因为如果变量值为`null`，使用非严格相等也会返回`true`。

```js
var foo;
console.log(foo); // undefined
console.log(foo === undefined); // true
console.log(typeof foo === 'undefined'); // true

console.log(foo == null); // true. 错误，不要使用非严格相等！

function bar() {}
var baz = bar();
console.log(baz); // undefined
```

`null`只能被显式赋值给变量。它表示`空值`，与被显式赋值 `undefined` 的意义不同。要检查判断`null`值，需要使用严格相等运算符。请注意，和前面一样，不能使用非严格相等（`==`）来检查，因为如果变量值为`undefined`，使用非严格相等也会返回`true`。

```js
var foo = null;
console.log(foo === null); // true

console.log(foo == undefined); // true. 错误，不要使用非严格相等！
```

作为一种个人习惯，我从不使用未声明变量。如果定义了暂时没有用到的变量，我会在声明后明确地给它们赋值为`null`。

##### 什么是闭包 (closure)，如何使用它，为什么要使用它？

闭包是函数和声明该函数的词法环境的组合。词法作用域中使用的域，是变量在代码中声明的位置所决定的。闭包是即使被外部函数返回，依然可以访问到外部（封闭）函数作用域的函数。

**为什么使用闭包？**

* 利用闭包实现数据私有化或模拟私有方法。这个方式也称为[模块模式（module pattern）](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#modulepatternjavascript)。
* [部分参数函数（partial applications）柯里化（currying）](https://medium.com/javascript-scene/curry-or-partial-application-8150044c78b8#.l4b6l1i3x).

##### 请举出一个匿名函数的典型用例？

匿名函数可以在 IIFE 中使用，来封装局部作用域内的代码，以便其声明的变量不会暴露到全局作用域。

```js
(function() {
  // 一些代码。
})();
```

匿名函数可以作为只用一次，不需要在其他地方使用的回调函数。当处理函数在调用它们的程序内部被定义时，代码具有更好地自闭性和可读性，可以省去寻找该处理函数的函数体位置的麻烦。

```js
setTimeout(function() {
  console.log('Hello world!');
}, 1000);
```

匿名函数可以用于函数式编程或 Lodash（类似于回调函数）。

```js
const arr = [1, 2, 3];
const double = arr.map(function(el) {
  return el * 2;
});
console.log(double); // [2, 4, 6]
```

##### 你是如何组织自己的代码？是使用模块模式，还是使用经典继承的方法？

我以前使用 Backbone 组织我的模型（model），Backbone 鼓励采用面向对象的方法——创建 Backbone 模型，并为其添加方法。

模块模式仍然是很好的方式，但是现在我使用基于 React/Redux 的 Flux 体系结构，它鼓励使用单向函数编程的方法。我用普通对象（plain object）表示我的 app 模型，编写实用纯函数去操作这些对象。使用动作（actions）和化简器（reducers）来处理状态，就像其他 Redux 应用一样。

我尽可能避免使用经典继承。如果非要这么做，我会坚持[这些原则](https://medium.com/@dan_abramov/how-to-use-classes-and-sleep-at-night-9af8de78ccb4)。

##### 请指出 JavaScript 宿主对象 (host objects) 和原生对象 (native objects) 的区别？

原生对象是由 ECMAScript 规范定义的 JavaScript 内置对象，比如`String`、`Math`、`RegExp`、`Object`、`Function`等等。

宿主对象是由运行时环境（浏览器或 Node）提供，比如`window`、`XMLHTTPRequest`等等。

##### 请指出以下代码的区别：`function Person(){}`、`var person = Person()`、`var person = new Person()`？

这个问题问得很含糊。我猜这是在考察 JavaScript 中的构造函数（constructor）。从技术上讲，`function Person(){}`只是一个普通的函数声明。使用 PascalCase 方式命名函数作为构造函数，是一个惯例。

`var person = Person()`将`Person`以普通函数调用，而不是构造函数。如果该函数是用作构造函数的，那么这种调用方式是一种常见错误。通常情况下，构造函数不会返回任何东西，因此，像普通函数一样调用构造函数，只会返回`undefined`赋给用作实例的变量。

`var person = new Person()`使用`new`操作符，创建`Person`对象的实例，该实例继承自`Person.prototype`。另外一种方式是使用`Object.create`，例如：Object.create(Person.prototype)`。

```js
function Person(name) {
  this.name = name;
}

var person = Person('John');
console.log(person); // undefined
console.log(person.name); // Uncaught TypeError: Cannot read property 'name' of undefined

var person = new Person('John');
console.log(person); // Person { name: "John" }
console.log(person.name); // "john"
```

##### `.call` 和 `.apply` 的区别是什么？

`.call`和`.apply`都用于调用函数，第一个参数将用作函数内 this 的值。然而，`.call`接受逗号分隔的参数作为后面的参数，而`.apply`接受一个参数数组作为后面的参数。一个简单的记忆方法是，从`call`中的 C 联想到逗号分隔（comma-separated），从`apply`中的 A 联想到数组（array）。

```js
function add(a, b) {
  return a + b;
}

console.log(add.call(null, 1, 2)); // 3
console.log(add.apply(null, [1, 2])); // 3
```

##### 请解释 `Function.prototype.bind`？

摘自[MDN](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind)：

> `bind()`方法创建一个新的函数, 当被调用时，将其 this 关键字设置为提供的值，在调用新函数时，在任何提供之前提供一个给定的参数序列。

根据我的经验，将`this`的值绑定到想要传递给其他函数的类的方法中是非常有用的。在 React 组件中经常这样做。

##### 在什么时候你会使用 `document.write()`？

`document.write()`用来将一串文本写入由`document.open()`打开的文档流中。当页面加载后执行`document.write()`时，它将调用`document.open`，会清除整个文档（`<head>`和`<body>`会被移除！），并将文档内容替换成给定的字符串参数。因此它通常被认为是危险的并且容易被误用。

网上有一些答案，解释了`document.write()`被用于分析代码中，或者[当你想包含只有在启用了 JavaScript 的情况下才能工作的样式](https://www.quirksmode.org/blog/archives/2005/06/three_javascrip_1.html)。它甚至在 HTML5 样板代码中用于[并行加载脚本并保持执行顺序](https://github.com/paulirish/html5-boilerplate/wiki/Script-Loading-Techniques#documentwrite-script-tag)！但是，我怀疑这些使用原因是过时的，现在可以在不使用`document.write()`的情况下实现。如果我的观点有错，请纠正我。

##### 请指出浏览器特性检测，特性推断和浏览器 UA 字符串嗅探的区别？

**功能检测（feature detection）**

功能检测包括确定浏览器是否支持某段代码，以及是否运行不同的代码（取决于它是否执行），以便浏览器始终能够正常运行代码功能，而不会在某些浏览器中出现崩溃和错误。例如：

```js
if ('geolocation' in navigator) {
  // 可以使用 navigator.geolocation
} else {
  // 处理 navigator.geolocation 功能缺失
}
```

[Modernizr](https://modernizr.com/)是处理功能检测的优秀工具。

**功能推断（feature inference）**

功能推断与功能检测一样，会对功能可用性进行检查，但是在判断通过后，还会使用其他功能，因为它假设其他功能也可用，例如：

```js
if (document.getElementsByTagName) {
  element = document.getElementById(id);
}
```

非常不推荐这种方式。功能检测更能保证万无一失。

**UA 字符串**

这是一个浏览器报告的字符串，它允许网络协议对等方（network protocol peers）识别请求用户代理的应用类型、操作系统、应用供应商和应用版本。它可以通过`navigator.userAgent`访问。 然而，这个字符串很难解析并且很可能存在欺骗性。例如，Chrome 会同时作为 Chrome 和 Safari 进行报告。因此，要检测 Safari，除了检查 Safari 字符串，还要检查是否存在 Chrome 字符串。不要使用这种方式。

##### 请尽可能详尽的解释 Ajax 的工作原理。

Ajax（asynchronous JavaScript and XML）是使用客户端上的许多 Web 技术，创建异步 Web 应用的一种 Web 开发技术。借助 Ajax，Web 应用可以异步（在后台）向服务器发送数据和从服务器检索数据，而不会干扰现有页面的显示和行为。通过将数据交换层与表示层分离，Ajax 允许网页和扩展 Web 应用程序动态更改内容，而无需重新加载整个页面。实际上，现在通常将 XML 替换为 JSON，因为 JavaScript 对 JSON 有原生支持优势。

`XMLHttpRequest` API 经常用于异步通信。此外还有最近流行的`fetch` API。

##### 使用 Ajax 都有哪些优劣？

**优点**

* 交互性更好。来自服务器的新内容可以动态更改，无需重新加载整个页面。
* 减少与服务器的连接，因为脚本和样式只需要被请求一次。
* 状态可以维护在一个页面上。JavaScript 变量和 DOM 状态将得到保持，因为主容器页面未被重新加载。
* 基本上包括大部分 SPA 的优点。

**缺点**

* 动态网页很难收藏。
* 如果 JavaScript 已在浏览器中被禁用，则不起作用。
* 有些网络爬虫不执行 JavaScript，也不会看到 JavaScript 加载的内容。
* 基本上包括大部分 SPA 的缺点。

##### 请解释 JSONP 的工作原理，以及它为什么不是真正的 Ajax。

JSONP（带填充的 JSON）是一种通常用于绕过 Web 浏览器中的跨域限制的方法，因为 Ajax 不允许跨域请求。

JSONP 通过`<script>`标签发送跨域请求，通常使用`callback`查询参数，例如：`https://example.com?callback=printData`。 然后服务器将数据包装在一个名为`printData`的函数中并将其返回给客户端。

```html
<!-- https://mydomain.com -->
<script>
function printData(data) {
  console.log(`My name is ${data.name}!`);
}
</script>

<script src="https://example.com?callback=printData"></script>
```

```js
// 文件加载自 https://example.com?callback=printData
printData({ name: 'LI Jialin' });
```

客户端必须在其全局范围内具有`printData`函数，并且在收到来自跨域的响应时，该函数将由客户端执行。

JSONP 可能具有一些安全隐患。由于 JSONP 是纯 JavaScript 实现，它可以完成 JavaScript 所能做的一切，因此需要信任 JSONP 数据的提供者。

现如今，[跨来源资源共享（CORS）](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing) 是推荐的主流方式，JSONP 已被视为一种比较 hack 的方式。

##### 你使用过 JavaScript 模板系统吗？
  ###### 如有使用过，请谈谈你都使用过哪些库？

使用过。Handlebars、Underscore、Lodash、AngularJS 和 JSX。我不喜欢 AngularJS 中的模板，因为它在指令中大量使用了字符串，并且书写错误会被忽略。JSX 是我的新宠，因为它更接近 JavaScript，几乎没有什么学习成本。现在，可以使用 ES2015 模板字符串快速创建模板，而不需依赖第三方代码。

```js
const template = `<div>My name is: ${name}</div>`;
```

但是，请注意上述方法中可能存在的 XSS，因为内容不会被转义，与模板库不同

##### 请解释变量声明提升 (hoisting)。

变量提升（hoisting）是用于解释代码中变量声明行为的术语。使用`var`关键字声明或初始化的变量，会将声明语句“提升”到当前作用域的顶部。 但是，只有声明才会触发提升，赋值语句（如果有的话）将保持原样。我们用几个例子来解释一下。

```js
// 用 var 声明得到提升
console.log(foo); // undefined
var foo = 1;
console.log(foo); // 1

// 用 let/const 声明不会提升
console.log(bar); // ReferenceError: bar is not defined
let bar = 2;
console.log(bar); // 2
```

函数声明会使函数体提升，但函数表达式（以声明变量的形式书写）只有变量声明会被提升。

```js
// 函数声明
console.log(foo); // [Function: foo]
foo(); // 'FOOOOO'
function foo() {
  console.log('FOOOOO');
}
console.log(foo); // [Function: foo]

// 函数表达式
console.log(bar); // undefined
bar(); // Uncaught TypeError: bar is not a function
var bar = function() {
  console.log('BARRRR');
};
console.log(bar); // [Function: bar]
```

##### 请描述事件冒泡机制 (event bubbling)。

当一个事件在 DOM 元素上触发时，如果有事件监听器，它将尝试处理该事件，然后事件冒泡到其父级元素，并发生同样的事情。最后直到事件到达祖先元素。事件冒泡是实现事件委托的原理（event delegation）。

##### "attribute" 和 "property" 的区别是什么？

“Attribute” 是在 HTML 中定义的，而 “property” 是在 DOM 上定义的。为了说明区别，假设我们在 HTML 中有一个文本框：`<input type="text" value="Hello">`。

```js
const input = document.querySelector('input');
console.log(input.getAttribute('value')); // Hello
console.log(input.value); // Hello
```

但是在文本框中键入“ World!”后:

```js
console.log(input.getAttribute('value')); // Hello
console.log(input.value); // Hello World!
```

##### 为什么扩展 JavaScript 内置对象不是好的做法？

扩展 JavaScript 内置（原生）对象意味着将属性或方法添加到其`prototype`中。虽然听起来很不错，但事实上这样做很危险。想象一下，你的代码使用了一些库，它们通过添加相同的 contains 方法来扩展`Array.prototype`，如果这两个方法的行为不相同，那么这些实现将会相互覆盖，你的代码将不能正常运行。

扩展内置对象的唯一使用场景是创建 polyfill，本质上为老版本浏览器缺失的方法提供自己的实现，该方法是由 JavaScript 规范定义的。

##### 请指出 document load 和 document DOMContentLoaded 两个事件的区别。

当初始的 HTML 文档被完全加载和解析完成之后，`DOMContentLoaded`事件被触发，而无需等待样式表、图像和子框架的完成加载。

`window`的`load`事件仅在 DOM 和所有相关资源全部完成加载后才会触发。

##### `==` 和 `===` 有什么不同？

`==`是抽象相等运算符，而`===`是严格相等运算符。`==`运算符是在进行必要的类型转换后，再比较。`===`运算符不会进行类型转换，所以如果两个值不是相同的类型，会直接返回`false`。使用`==`时，可能发生一些特别的事情，例如：

```js
1 == '1'; // true
1 == [1]; // true
1 == true; // true
0 == ''; // true
0 == '0'; // true
0 == false; // true
```

我的建议是从不使用`==`运算符，除了方便与`null`或`undefined`比较时，`a == null`如果`a`为`null`或`undefined`将返回`true`。

```js
var a = null;
console.log(a == null); // true
console.log(a == undefined); // true
```

##### 请解释 JavaScript 的同源策略 (same-origin policy)。

同源策略可防止 JavaScript 发起跨域请求。源被定义为 URI、主机名和端口号的组合。此策略可防止页面上的恶意脚本通过该页面的文档对象模型，访问另一个网页上的敏感数据。

##### 如何实现下列代码：
```javascript
[1,2,3,4,5].duplicator(); // [1,2,3,4,5,1,2,3,4,5]
```

```js
function duplicate(arr) {
  return arr.concat(arr);
}

duplicate([1, 2, 3, 4, 5]); // [1,2,3,4,5,1,2,3,4,5]
```

##### 什么是三元表达式 (Ternary expression)？“三元 (Ternary)” 表示什么意思？

“三元”表示接受三个操作数：判断条件，`then`表达式和`else`表达式。三元表达式不是 JavaScript 特有的，我不知道这个问题为什么会出现在这里。

##### 什么是 `"use strict";` ? 使用它的好处和坏处分别是什么？

'use strict' 是用于对整个脚本或单个函数启用严格模式的语句。严格模式是可选择的一个限制 JavaScript 的变体一种方式 。

**优点：**

* 无法再意外创建全局变量。
* 会使引起静默失败（silently fail，即：不报错也没有任何效果）的赋值操抛出异常。
* 试图删除不可删除的属性时会抛出异常（之前这种操作不会产生任何效果）。
* 要求函数的参数名唯一。
* 全局作用域下，`this`的值为`undefined`。
* 捕获了一些常见的编码错误，并抛出异常。
* 禁用令人困惑或欠佳的功能。

**缺点：**

* 缺失许多开发人员已经习惯的功能。
* 无法访问`function.caller`和`function.arguments`。
* 以不同严格模式编写的脚本合并后可能导致问题。

总的来说，我认为利大于弊，我从来不使用严格模式禁用的功能，因此我推荐使用严格模式。

##### 请实现一个遍历至 `100` 的 for loop 循环，在能被 `3` 整除时输出 **"fizz"**，在能被 `5` 整除时输出 **"buzz"**，在能同时被 `3` 和 `5` 整除时输出 **"fizzbuzz"**。

来自 [Paul Irish](https://gist.github.com/jaysonrowe/1592432#gistcomment-790724)的 FizzBuzz。

```js
for (let i = 1; i <= 100; i++) {
  let f = i % 3 == 0,
    b = i % 5 == 0;
  console.log(f ? (b ? 'FizzBuzz' : 'Fizz') : b ? 'Buzz' : i);
}
```

我不建议你在面试时写上面的代码。只要写得清晰即可。关于更多千奇百怪的 FizzBuzz 实现，请查看下面的参考链接。

##### 为何通常会认为保留网站现有的全局作用域 (global scope) 不去改变它，是较好的选择？

每个脚本都可以访问全局作用域，如果人人都使用全局命名空间来定义自己的变量，肯定会发生冲突。使用模块模式（IIFE）将变量封装在本地命名空间中。

##### 为何你会使用 `load` 之类的事件 (event)？此事件有缺点吗？你是否知道其他替代品，以及为何使用它们？

在文档装载完成后会触发`load`事件。此时，在文档中的所有对象都在 DOM 中，所有图像、脚本、链接和子框架都完成了加载。

DOM 事件`DOMContentLoaded`将在页面的 DOM 构建完成后触发，但不要等待其他资源完成加载。如果在初始化之前不需要装入整个页面，这个事件是使用首选。

TODO.

##### 请解释什么是单页应用 (single page app), 以及如何使其对搜索引擎友好 (SEO-friendly)。

以下摘自 [Grab Front End Guide](https://github.com/grab/front-end-guide)，碰巧的是，这正是我自己写的！

现如今，Web 开发人员将他们构建的产品称为 Web 应用，而不是网站。虽然这两个术语之间没有严格的区别，但网络应用往往具有高度的交互性和动态性，允许用户执行操作并接收他们的操作响应。在过去，浏览器从服务器接收 HTML 并渲染。当用户导航到其它 URL 时，需要整页刷新，服务器会为新页面发送新的 HTML。这被称为服务器端渲染。

然而，在现代的 SPA 中，客户端渲染取而代之。浏览器从服务器加载初始页面、整个应用程序所需的脚本（框架、库、应用代码）和样式表。当用户导航到其他页面时，不会触发页面刷新。该页面的 URL 通过 [HTML5 History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API) 进行更新。浏览器通过 [AJAX](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started) 请求向服务器检索新页面所需的数据（通常采用 JSON 格式）。然后，SPA 通过 JavaScript 来动态更新页面，这些 JavaScript 在初始页面加载时已经下载。这种模式类似于原生移动应用的工作方式。

**好处：**

* 用户感知响应更快，用户切换页面时，不再看到因页面刷新而导致的白屏。
* 对服务器进行的 HTTP 请求减少，因为对于每个页面加载，不必再次下载相同的资源。
* 客户端和服务器之间的关注点分离。可以为不同平台（例如手机、聊天机器人、智能手表）建立新的客户端，而无需修改服务器代码。只要 API 没有修改，可以单独修改客户端和服务器上的代码。

**坏处：**

* 由于加载了多个页面所需的框架、应用代码和资源，导致初始页面加载时间较长。
* 服务器还需要进行额外的工作，需要将所有请求路由配置到单个入口点，然后由客户端接管路由。
* SPA 依赖于 JavaScript 来呈现内容，但并非所有搜索引擎都在抓取过程中执行 JavaScript，他们可能会在你的页面上看到空的内容。这无意中损害了应用的搜索引擎优化（SEO）。然而，当你构建应用时，大多数情况下，搜索引擎优化并不是最重要的因素，因为并非所有内容都需要通过搜索引擎进行索引。为了解决这个问题，可以在服务器端渲染你的应用，或者使用诸如 [Prerender](https://prerender.io/) 的服务来“在浏览器中呈现你的 javascript，保存静态 HTML，并将其返回给爬虫”。

##### 你使用过 Promises 及其 polyfills 吗? 请写出 Promise 的基本用法（ES6）。

掌握它的工作原理。`Promise`是一个可能在未来某个时间产生结果的对象：操作成功的结果或失败的原因（例如发生网络错误）。 `Promise`可能处于以下三种状态之一：fulfilled、rejected 或 pending。 用户可以对`Promise`添加回调函数来处理操作成功的结果或失败的原因。

一些常见的 polyfill 是`$.deferred`、Q 和 Bluebird，但不是所有的 polyfill 都符合规范。ES2015 支持 Promises，现在通常不需要使用 polyfills。

##### 使用 Promises 而非回调 (callbacks) 优缺点是什么？

**优点：**

* 避免可读性极差的回调地狱。
* 使用`.then()`编写的顺序异步代码，既简单又易读。
* 使用`Promise.all()`编写并行异步代码变得很容易。

**缺点：**

* 轻微地增加了代码的复杂度（这点存在争议）。
* 在不支持 ES2015 的旧版浏览器中，需要引入 polyfill 才能使用。

##### 使用一种可以编译成 JavaScript 的语言来写 JavaScript 代码有哪些优缺点？

Some examples of languages that compile to JavaScript include CoffeeScript, Elm, ClojureScript, PureScript and TypeScript.
这些是转译成 JavaScript 的语言，包括 CoffeeScript、Elm、ClojureScript、PureScript 和 TypeScript。

**优点：**

* 修复了 JavaScript 中的一些长期问题，并摒弃了 JavaScript 不好的做法。
* 在 JavaScript 的基础上提供一些语法糖，使我们能够编写更短的代码，我认为 ES5 缺乏语法糖的支持，但 ES2015 非常好。
* 对于需要长时间维护的大型项目，静态类型非常好用（针对 TypeScript）。

**缺点：**

* 由于浏览器只运行 JavaScript，所以需要构建、编译过程，在将代码提供给浏览器之前，需要将代码转译为 JavaScript。
* 如果 source map 不能很好地映射到预编译的源代码，调试会很痛苦。
* 大多数开发人员不熟悉这些语言，需要学习它。如果将其用于项目，会增加团队成本。
* 社区比较小（取决于语言），这意味着资源、教程、图书和工具难以找到。
* 可能缺乏 IDE（编辑器）的支持。
* 这些语言将始终落后于最新的 JavaScript 标准。
* 开发人员应该清楚代码正在被编译到什么地方——因为这是实际运行的内容，是最重要的。

实际上，ES2015 已经大大改进了 JavaScript，编写体验很好。我现在还没有真正看到对 CoffeeScript 的需求。

##### 你使用哪些工具和技术来调试 JavaScript 代码？

* React 和 Redux
  * [React Devtools](https://github.com/facebook/react-devtools)
  * [Redux Devtools](https://github.com/gaearon/redux-devtools)
* Vue
  * [Vue Devtools](https://github.com/vuejs/vue-devtools)
* JavaScript
  * [Chrome Devtools](https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d)
  * `debugger`声明
  * 使用万金油`console.log`进行调试

##### 你会使用怎样的语言结构来遍历对象属性 (object properties) 和数组内容？

**对象：**

* `for`循环：`for (var property in obj) { console.log(property); }`。但是，这还会遍历到它的继承属性，在使用之前，你需要加入`obj.hasOwnProperty(property)`检查。
* `Object.keys()`：`Object.keys(obj).forEach(function (property) { ... })`。`Object.keys()`方法会返回一个由一个给定对象的自身可枚举属性组成的数组。
* `Object.getOwnPropertyNames()`：`Object.getOwnPropertyNames(obj).forEach(function (property) { ... })`。`Object.getOwnPropertyNames()`方法返回一个由指定对象的所有自身属性的属性名（包括不可枚举属性但不包括 Symbol 值作为名称的属性）组成的数组。

**数组：**

* `for` loops：`for (var i = 0; i < arr.length; i++)`。这里的常见错误是`var`是函数作用域而不是块级作用域，大多数时候你想要迭代变量在块级作用域中。ES2015 引入了具有块级作用域的`let`，建议使用它。所以就变成了：`for (let i = 0; i < arr.length; i++)`。
* `forEach`：`arr.forEach(function (el, index) { ... })`。这个语句结构有时会更精简，因为如果你所需要的只是数组元素，你不必使用`index`。还有`every`和`some`方法可以让你提前终止遍历。

大多数情况下，我更喜欢`.forEach`方法，但这取决于你想要做什么。`for`循环有更强的灵活性，比如使用`break`提前终止循环，或者递增步数大于一。

##### 请解释可变 (mutable) 和不变 (immutable) 对象的区别。
  ###### 请举出 JavaScript 中一个不变性对象 (immutable object) 的例子？
  ###### 不变性 (immutability) 有哪些优缺点？
  ###### 如何用你自己的代码来实现不变性 (immutability)？

**_可变对象_** 在创建之后是可以被改变的。

**_不可变对象_** 在创建之后是不可以被改变的。

1. 在 `JavaScript` 中，`string` 和 `number` 从设计之初就是不可变(Immutable)。
2. **_不可变_** 其实是保持一个对象状态不变，这样做的好处是使得开发更加简单，可回溯，测试友好，减少了任何可能的副作用。但是，每当你想添加点东西到一个不可变(Immutable)对象里时，它一定是先拷贝已存在的值到新实例里，然后再给新实例添加内容，最后返回新实例。相比可变对象，这势必会有更多内存、计算量消耗。
3. 比如：构造一个纯函数

```js
const student1 = {
  school: 'Baidu',
  name: 'HOU Ce',
  birthdate: '1995-12-15',
};

const changeStudent = (student, newName, newBday) => {
  return {
    ...student, // 使用解构
    name: newName, // 覆盖name属性
    birthdate: newBday, // 覆盖birthdate属性
  };
};

const student2 = changeStudent(student1, 'YAN Haijing', '1990-11-10');

// both students will have the name properties
console.log(student1, student2);
// Object {school: "Baidu", name: "HOU Ce", birthdate: "1995-12-15"}
// Object {school: "Baidu", name: "YAN Haijing", birthdate: "1990-11-10"}
```

##### 请解释同步 (synchronous) 和异步 (asynchronous) 函数的区别。

同步函数阻塞，而异步函数不阻塞。在同步函数中，语句完成后，下一句才执行。在这种情况下，程序可以按照语句的顺序进行精确评估，如果其中一个语句需要很长时间，程序的执行会停滞很长时间。

异步函数通常接受回调作为参数，在调用异步函数后立即继续执行下一行。回调函数仅在异步操作完成且调用堆栈为空时调用。诸如从 Web 服务器加载数据或查询数据库等重负载操作应该异步完成，以便主线程可以继续执行其他操作，而不会出现一直阻塞，直到费时操作完成的情况（在浏览器中，界面会卡住）。

##### 什么是事件循环 (event loop)？
  ###### 请问调用栈 (call stack) 和任务队列 (task queue) 的区别是什么？

事件循环是一个单线程循环，用于监视调用堆栈并检查是否有工作即将在任务队列中完成。如果调用堆栈为空并且任务队列中有回调函数，则将回调函数出队并推送到调用堆栈中执行。

如果你没有看过 Philip Robert [关于事件循环的演讲](https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html)，你应该看一下。这是观看次数最多的 JavaScript 相关视频之一。

##### 解释 `function foo() {}` 与 `var foo = function() {}` 用法的区别

前者是函数声明，后者是函数表达式。关键的区别在于函数声明会使函数体提升（具有与变量相同的提升行为），但函数表达式的函数体不能。有关变量提升的更多解释，请参阅上面关于变量提升的问题。如果你试图在定义函数表达式之前调用它，你会得到一个`Uncaught TypeError: XXX is not a function`的错误。

**函数声明**

```js
foo(); // 'FOOOOO'
function foo() {
  console.log('FOOOOO');
}
```

**函数表达式**

```js
foo(); // Uncaught TypeError: foo is not a function
var foo = function() {
  console.log('FOOOOO');
};
```

##### 使用`let`、`var`和`const`创建变量有什么区别？

用`var`声明的变量的作用域是它当前的执行上下文，它可以是嵌套的函数，也可以是声明在任何函数外的变量。`let`和`const`是块级作用域，意味着它们只能在最近的一组花括号（function、if-else 代码块或 for 循环中）中访问。

```js
function foo() {
  // 所有变量在函数中都可访问
  var bar = 'bar';
  let baz = 'baz';
  const qux = 'qux';

  console.log(bar); // bar
  console.log(baz); // baz
  console.log(qux); // qux
}

console.log(bar); // ReferenceError: bar is not defined
console.log(baz); // ReferenceError: baz is not defined
console.log(qux); // ReferenceError: qux is not defined
```

```js
if (true) {
  var bar = 'bar';
  let baz = 'baz';
  const qux = 'qux';
}

// 用 var 声明的变量在函数作用域上都可访问
console.log(bar); // bar
// let 和 const 定义的变量在它们被定义的语句块之外不可访问
console.log(baz); // ReferenceError: baz is not defined
console.log(qux); // ReferenceError: qux is not defined
```

`var`会使变量提升，这意味着变量可以在声明之前使用。`let`和`const`不会使变量提升，提前使用会报错。

```js
console.log(foo); // undefined

var foo = 'foo';

console.log(baz); // ReferenceError: can't access lexical declaration 'baz' before initialization

let baz = 'baz';

console.log(bar); // ReferenceError: can't access lexical declaration 'bar' before initialization

const bar = 'bar';
```

用`var`重复声明不会报错，但`let`和`const`会。

```js
var foo = 'foo';
var foo = 'bar';
console.log(foo); // "bar"

let baz = 'baz';
let baz = 'qux'; // Uncaught SyntaxError: Identifier 'baz' has already been declared
```

`let`和`const`的区别在于：`let`允许多次赋值，而`const`只允许一次。

```js
// 这样不会报错。
let foo = 'foo';
foo = 'bar';

// 这样会报错。
const baz = 'baz';
baz = 'qux';
```

##### ES6 的类和 ES5 的构造函数有什么区别？

TODO

##### 你能给出一个使用箭头函数的例子吗，箭头函数与其他函数有什么不同？

TODO

##### 在构造函数中使用箭头函数有什么好处？

TODO

##### 高阶函数（higher-order）的定义是什么？

高阶函数是将一个或多个函数作为参数的函数，它用于数据处理，也可能将函数作为返回结果。高阶函数是为了抽象一些重复执行的操作。一个典型的例子是`map`，它将一个数组和一个函数作为参数。`map`使用这个函数来转换数组中的每个元素，并返回一个包含转换后元素的新数组。JavaScript 中的其他常见示例是`forEach`、`filter`和`reduce`。高阶函数不仅需要操作数组的时候会用到，还有许多函数返回新函数的用例。`Function.prototype.bind`就是一个例子。

**Map 示例：**

假设我们有一个由名字组成的数组，我们需要将每个字符转换为大写字母。

```js
const names = ['irish', 'daisy', 'anna'];
```

不使用高阶函数的方法是这样：

```js
const transformNamesToUppercase = function(names) {
  const results = [];
  for (let i = 0; i < names.length; i++) {
    results.push(names[i].toUpperCase());
  }
  return results;
};
transformNamesToUppercase(names); // ['IRISH', 'DAISY', 'ANNA']
```

使用`.map(transformerFn)`使代码更简明

```js
const transformNamesToUppercase = function(names) {
  return names.map(name => name.toUpperCase());
};
transformNamesToUppercase(names); // ['IRISH', 'DAISY', 'ANNA']
```

##### 请给出一个解构（destructuring）对象或数组的例子。

解构是 ES6 中新功能，它提供了一种简洁方便的方法来提取对象或数组的值，并将它们放入不同的变量中。

**数组解构**

```js
// 变量赋值
const foo = ['one', 'two', 'three'];

const [one, two, three] = foo;
console.log(one); // "one"
console.log(two); // "two"
console.log(three); // "three"
```

```js
// 变量交换
let a = 1;
let b = 3;

[a, b] = [b, a];
console.log(a); // 3
console.log(b); // 1
```

**对象解构**

```js
// 变量赋值
const o = { p: 42, q: true };
const { p, q } = o;

console.log(p); // 42
console.log(q); // true
```

##### ES6 的模板字符串为生成字符串提供了很大的灵活性，你可以举个例子吗？

**_模板字面量_**（Template literals） 是允许嵌入表达式的字符串字面量。你可以使用多行字符串和字符串插值功能。

**语法**

```js
`string text``string text line 1
 string text line 2``string text ${expression} string text`;

tag`string text ${expression} string text`;
```

**示例**

```js
console.log(`string text line 1
string text line 2`);
// "string text line 1
// string text line 2"

var a = 5;
var b = 10;
console.log(`Fifteen is ${a + b} and\nnot ${2 * a + b}.`);
// "Fifteen is 15 and
// not 20."
```

```js
//show函数采用rest参数的写法如下：

let name = '张三',
  age = 20,
  message = show`我来给大家介绍:${name}的年龄是${age}.`;

function show(stringArr, ...values) {
  let output = '';

  let index = 0;

  for (; index < values.length; index++) {
    output += stringArr[index] + values[index];
  }

  output += stringArr[index];

  return output;
}

message; //"我来给大家介绍:张三的年龄是20."
```

##### 你能举出一个柯里化函数（curry function）的例子吗？它有哪些好处？

柯里化（currying）是一种模式，其中具有多个参数的函数被分解为多个函数，当被串联调用时，将一次一个地累积所有需要的参数。这种技术帮助编写函数式风格的代码，使代码更易读、紧凑。值得注意的是，对于需要被 curry 的函数，它需要从一个函数开始，然后分解成一系列函数，每个函数都需要一个参数。

```js
function curry(fn) {
  if (fn.length === 0) {
    return fn;
  }

  function _curried(depth, args) {
    return function(newArgument) {
      if (depth - 1 === 0) {
        return fn(...args, newArgument);
      }
      return _curried(depth - 1, [...args, newArgument]);
    };
  }

  return _curried(fn.length, []);
}

function add(a, b) {
  return a + b;
}

var curriedAdd = curry(add);
var addFive = curriedAdd(5);

var result = [0, 1, 2, 3, 4, 5].map(addFive); // [5, 6, 7, 8, 9, 10]
```

##### 使用扩展运算符（spread）的好处是什么，它与使用剩余参数语句（rest）有什么区别？

在函数泛型编码时，ES6 的扩展运算符非常有用，因为我们可以轻松创建数组和对象的拷贝，而无需使用`Object.create`、`slice`或其他函数库。这个语言特性在 Redux 和 rx.js 的项目中经常用到。

```js
function putDookieInAnyArray(arr) {
  return [...arr, 'dookie'];
}

const result = putDookieInAnyArray(['I', 'really', "don't", 'like']); // ["I", "really", "don't", "like", "dookie"]

const person = {
  name: 'Todd',
  age: 29,
};

const copyOfTodd = { ...person };
```

ES6 的剩余参数语句提供了一个简写，允许我们将不定数量的参数表示为一个数组。它就像是扩展运算符语法的反面，将数据收集到数组中，而不是解构数组。剩余参数语句在函数参数、数组和对象的解构赋值中有很大作用。

```js
function addFiveToABunchOfNumbers(...numbers) {
  return numbers.map(x => x + 5);
}

const result = addFiveToABunchOfNumbers(4, 5, 6, 7, 8, 9, 10); // [9, 10, 11, 12, 13, 14, 15]

const [a, b, ...rest] = [1, 2, 3, 4]; // a: 1, b: 2, rest: [3, 4]

const { e, f, ...others } = {
  e: 1,
  f: 2,
  g: 3,
  h: 4,
}; // e: 1, f: 2, others: { g: 3, h: 4 }
```

##### 如何在文件之间共用代码？

这取决于执行 JavaScript 的环境。

在客户端（浏览器环境）上，只要变量或函数在全局作用域（`window`）中声明，所有脚本都可以引用它们。或者，通过 RequireJS 采用异步模块定义（AMD）以获得更多模块化方法。

在服务器（Node.js）上，常用的方法是使用 CommonJS。每个文件都被视为一个模块，可以通过将它们附加到`module.exports`对象来导出变量和函数。

ES2015 定义了一个模块语法，旨在替换 AMD 和 CommonJS。 这最终将在浏览器和 Node 环境中得到支持。

##### 什么情况下会用到静态类成员？

静态类成员（属性或方法）不绑定到某个类的特定实例，不管哪个实例引用它，都具有相同的值。静态属性通常是配置变量，而静态方法通常是纯粹的实用函数，不依赖于实例的状态。

#### <a name='testing-questions'>测试相关问题：</a>

* 对代码进行测试的有什么优缺点？
* 你会用什么工具测试你的代码功能？
* 单元测试与功能/集成测试的区别是什么？
* 代码风格 linting 工具的作用是什么？

#### <a name='performance-questions'>效能相关问题：</a>

* 你会用什么工具来查找代码中的性能问题？
* 你会用什么方式来增强网站的页面滚动效能？
* 请解释 layout、painting 和 compositing 的区别。

#### <a name='network-questions'>网络相关问题：</a>

* 为什么传统上利用多个域名来提供网站资源会更有效？
* 请尽可能完整得描述从输入 URL 到整个网页加载完毕及显示在屏幕上的整个流程。
* Long-Polling、Websockets 和 Server-Sent Event 之间有什么区别？
* 请描述以下 request 和 response headers：
  * Diff. between Expires, Date, Age and If-Modified-...
  * Do Not Track
  * Cache-Control
  * Transfer-Encoding
  * ETag
  * X-Frame-Options
* 什么是 HTTP method？请罗列出你所知道的所有 HTTP method，并给出解释。
* 请解释 HTTP status 301 与 302 的区别？

#### <a name='coding-questions'>代码相关的问题：</a>

*问题：`foo`的值是什么？*
```javascript
var foo = 10 + '20';
```

*问题：如何实现以下函数？*
```javascript
add(2, 5); // 7
add(2)(5); // 7
```

*问题：下面的语句的返回值是什么？*
```javascript
"i'm a lasagna hog".split("").reverse().join("");
```

*问题：`window.foo`的值是什么？*
```javascript
( window.foo || ( window.foo = "bar" ) );
```

*问题：下面两个 alert 的结果是什么？*
```javascript
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```

*问题：`foo.length`的值是什么？*
```javascript
var foo = [];
foo.push(1);
foo.push(2);
```

*问题：`foo.x`的值是什么？*
```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```

*问题：下面代码的输出是什么？*
```javascript
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
console.log('three');
```

#### <a name='fun-questions'>趣味问题：</a>

* 你最近写过什么的很酷的项目吗？
* 在你使用的开发工具中，最喜欢哪些方面？
* 谁使你踏足了前端开发领域？
* 你有什么业余项目吗？是哪种类型的？
* 你最爱的 IE 特性是什么？
* 你对咖啡有没有什么喜好？


#### <a name='contributors'>贡献者：</a>

本文档始于 2009 年，是以下作者的合作成果：[@paul_irish](https://twitter.com/paul_irish) [@bentruyman](https://twitter.com/bentruyman) [@cowboy](https://twitter.com/cowboy) [@ajpiano](https://twitter.com/ajpiano) [@SlexAxton](https://twitter.com/slexaxton) [@boazsender](https://twitter.com/boazsender) [@miketaylr](https://twitter.com/miketaylr) [@vladikoff](https://twitter.com/vladikoff) [@gf3](https://twitter.com/gf3) [@jon_neal](https://twitter.com/jon_neal) [@sambreed](https://twitter.com/sambreed) 和 [@iansym](https://twitter.com/iansym)。

时至今日，文档已经融入超过 [100 位开发者](https://github.com/h5bp/Front-end-Developer-Interview-Questions/graphs/contributors)的贡献。
