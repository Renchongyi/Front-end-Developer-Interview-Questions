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

* CSS 中类 (classes) 和 ID 的区别。
* 请问 "resetting" 和 "normalizing" CSS 之间的区别？你会如何选择，为什么？
* 请解释浮动 (Floats) 及其工作原理。
* 描述`z-index`和叠加上下文是如何形成的。
* 请描述 BFC(Block Formatting Context) 及其如何工作。
* 列举不同的清除浮动的技巧，并指出它们各自适用的使用场景。
* 请解释 CSS sprites，以及你要如何在页面或网站中实现它。
* 你最喜欢的图片替换方法是什么，你如何选择使用。
* 你会如何解决特定浏览器的样式问题？
* 如何为有功能限制的浏览器提供网页？
  * 你会使用哪些技术和处理方法？
* 有哪些的隐藏内容的方法 (如果同时还要保证屏幕阅读器可用呢)？
* 你用过栅格系统 (grid system) 吗？如果使用过，你最喜欢哪种？
* 你用过媒体查询，或针对移动端的布局/CSS 吗？
* 你熟悉 SVG 样式的书写吗？
* 如何优化网页的打印样式？
* 在书写高效 CSS 时会有哪些问题需要考虑？
* 使用 CSS 预处理器的优缺点有哪些？
  * 请描述你曾经使用过的 CSS 预处理器的优缺点。
* 如果设计中使用了非标准的字体，你该如何去实现？
* 请解释浏览器是如何判断元素是否匹配某个 CSS 选择器？
* 请描述伪元素 (pseudo-elements) 及其用途。
* 请解释你对盒模型的理解，以及如何在 CSS 中告诉浏览器使用不同的盒模型来渲染你的布局。
* 请解释 ```* { box-sizing: border-box; }``` 的作用, 并且说明使用它有什么好处？
* 请罗列出你所知道的 display 属性的全部值
* 请解释 inline 和 inline-block 的区别？
* 请解释 relative、fixed、absolute 和 static 元素的区别
* CSS 中字母 'C' 的意思是叠层 (Cascading)。请问在确定样式的过程中优先级是如何决定的 (请举例)？如何有效使用此系统？
* 你在开发或生产环境中使用过哪些 CSS 框架？你觉得应该如何改善他们？
* 请问你有尝试过 CSS Flexbox 或者 Grid 标准规格吗？
* 为什么响应式设计 (responsive design) 和自适应设计 (adaptive design) 不同？
* 你有兼容 retina 屏幕的经历吗？如果有，在什么地方使用了何种技术？
* 请问为何要使用 `translate()` 而非 *absolute positioning*，或反之的理由？为什么？

#### <a name='js-questions'>JS 相关问题：</a>

* 请解释事件代理 (event delegation)。
* 请解释 JavaScript 中 `this` 是如何工作的。
* 请解释原型继承 (prototypal inheritance) 的原理。
* 你怎么看 AMD vs. CommonJS？
* 请解释为什么接下来这段代码不是 IIFE (立即调用的函数表达式)：`function foo(){ }();`.
  * 要做哪些改动使它变成 IIFE?
* 描述以下变量的区别：`null`，`undefined` 或 `undeclared`？
  * 该如何检测它们？
* 什么是闭包 (closure)，如何使用它，为什么要使用它？
* 请举出一个匿名函数的典型用例？
* 你是如何组织自己的代码？是使用模块模式，还是使用经典继承的方法？
* 请指出 JavaScript 宿主对象 (host objects) 和原生对象 (native objects) 的区别？
* 请指出以下代码的区别：`function Person(){}`、`var person = Person()`、`var person = new Person()`？
* `.call` 和 `.apply` 的区别是什么？
* 请解释 `Function.prototype.bind`？
* 在什么时候你会使用 `document.write()`？
* 请指出浏览器特性检测，特性推断和浏览器 UA 字符串嗅探的区别？
* 请尽可能详尽的解释 Ajax 的工作原理。
* 使用 Ajax 都有哪些优劣？
* 请解释 JSONP 的工作原理，以及它为什么不是真正的 Ajax。
* 你使用过 JavaScript 模板系统吗？
  * 如有使用过，请谈谈你都使用过哪些库？
* 请解释变量声明提升 (hoisting)。
* 请描述事件冒泡机制 (event bubbling)。
* "attribute" 和 "property" 的区别是什么？
* 为什么扩展 JavaScript 内置对象不是好的做法？
* 请指出 document load 和 document DOMContentLoaded 两个事件的区别。
* `==` 和 `===` 有什么不同？
* 请解释 JavaScript 的同源策略 (same-origin policy)。
* 如何实现下列代码：
```javascript
[1,2,3,4,5].duplicator(); // [1,2,3,4,5,1,2,3,4,5]
```
* 什么是三元表达式 (Ternary expression)？“三元 (Ternary)” 表示什么意思？
* 什么是 `"use strict";` ? 使用它的好处和坏处分别是什么？
* 请实现一个遍历至 `100` 的 for loop 循环，在能被 `3` 整除时输出 **"fizz"**，在能被 `5` 整除时输出 **"buzz"**，在能同时被 `3` 和 `5` 整除时输出 **"fizzbuzz"**。
* 为何通常会认为保留网站现有的全局作用域 (global scope) 不去改变它，是较好的选择？
* 为何你会使用 `load` 之类的事件 (event)？此事件有缺点吗？你是否知道其他替代品，以及为何使用它们？
* 请解释什么是单页应用 (single page app), 以及如何使其对搜索引擎友好 (SEO-friendly)。
* 你使用过 Promises 及其 polyfills 吗? 请写出 Promise 的基本用法（ES6）。
* 使用 Promises 而非回调 (callbacks) 优缺点是什么？
* 使用一种可以编译成 JavaScript 的语言来写 JavaScript 代码有哪些优缺点？
* 你使用哪些工具和技术来调试 JavaScript 代码？
* 你会使用怎样的语言结构来遍历对象属性 (object properties) 和数组内容？
* 请解释可变 (mutable) 和不变 (immutable) 对象的区别。
  * 请举出 JavaScript 中一个不变性对象 (immutable object) 的例子？
  * 不变性 (immutability) 有哪些优缺点？
  * 如何用你自己的代码来实现不变性 (immutability)？
* 请解释同步 (synchronous) 和异步 (asynchronous) 函数的区别。
* 什么是事件循环 (event loop)？
  * 请问调用栈 (call stack) 和任务队列 (task queue) 的区别是什么？
* 解释 `function foo() {}` 与 `var foo = function() {}` 用法的区别

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
