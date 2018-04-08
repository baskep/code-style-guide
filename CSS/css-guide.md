# CSS Style Standard　

## Grammar(语法)
* 用两个空格来代替制表符（tab） -- 这是唯一能保证在所有环境下获得一致展现的方法。
* 为选择器分组时，将单独的选择器单独放在一行。
* 为了代码的易读性，在每个声明块的左花括号前添加一个空格。
* 声明块的右花括号应当单独成行。
* 为了获得更准确的错误报告，每条声明都应该独占一行。
* 所有声明语句都应当以分号结尾。
* 对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格
* 不要在 rgb()、rgba()、hsl()、hsla() 或 rect() 值的内部的逗号后面插入空格。这样利于从多个属性值（既加逗号也加空格）中区分多个颜色值（只加逗号，不加空格）。
* 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替 -0.5px）。
* 十六进制值应该全部小写，例如，#fff。在扫描文档时，小写字符易于分辨，因为他们的形式更易于区分。
* 尽量使用简写形式的十六进制值，例如，用 #fff 代替 #ffffff。
* 为选择器中的属性添加双引号，例如，input[type="text"]。只有在某些情况下是可选的，但是，为了代码的一致性，建议都加上双引号。
* 避免为 0 值指定单位，例如，用 margin: 0; 代替 margin: 0px;。

``` css
    /* Bad CSS */
    .selector, .selector-secondary, .selector[type=text] {
        padding:15px;
        margin:0px 0px 15px;
        background-color:rgba(0, 0, 0, 0.5);
        box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
    }

/* Good CSS */
    .selector,
    .selector-secondary,
    .selector[type="text"] {
        padding: 15px;
        margin-bottom: 15px;
        background-color: rgba(0,0,0,.5);
        box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
    }
  
```
## Declaration Order(声明顺序)
1.位置属性(position, top, right, z-index, display, float等)  
2.大小(width, height, padding, margin)  
3.文字系列(font, line-height, letter-spacing, color- text-align等)  
4.背景(background, border等)  
5.其他(animation, transition等)  
```css
    /* Bad CSS */
    .example {
        color: red;
        z-index: -1;
        width: 100px;
        background-color: #9e0;
        display: inline-block;
        height: 100px;
        font-size: 18px;
    }
    /* Good CSS */
    .example {
        z-index: -1;
        display: inline-block;
        width: 100px;
        height: 100px;
        font-size: 18px;
        color: red;
        background-color: #9e0;
    }
```
```css
    .declaration-order {
    /* Positioning */
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        z-index: 100;

    /* Box-model */
        display: block;
        float: right;
        width: 100px;
        height: 100px;

    /* Typography */
        font: normal 13px "Helvetica Neue", sans-serif;
        line-height: 1.5;
        color: #333;
        text-align: center;

    /* Visual */
        background-color: #f5f5f5;
        border: 1px solid #e5e5e5;
        border-radius: 3px;

    /* Misc */
        opacity: 1;
    }
```
## Simplify Style(简化样式)
在需要显示地设置所有值的情况下，应当尽量限制使用简写形式的属性声明。常见的滥用简写属性声明的情况如下：
* padding
* margin
* font
* background
* border
* border-radius
大部分情况下，我们不需要为简写形式的属性声明指定所有值。例如，HTML 的 heading 元素只需要设置上、下边距（margin）的值，因此，在必要的时候，只需覆盖这两个值就可以。过度使用简写形式的属性声明会导致代码混乱，并且会对属性值带来不必要的覆盖从而引起意外的副作用  

```css
    /* Bad CSS */
    .example {
        margin: 0 0 10px;
        font-family: serif;
        font-size: 100%;
        line-height: 1.6;
        background: red;
        background: url("image.jpg");
        border-radius: 3px 3px 0 0;
    }
    /* Good CSS */
    .example {
        margin-bottom: 10px;
        font: 100%/1.6 serif;
        background-color: red;
        background-image: url("image.jpg");
        border-top-left-radius: 3px;
        border-top-right-radius: 3px;
    }
```
## explian(注释)
代码是由人编写并维护的。请确保你的代码能够自描述、注释良好并且易于他人理解。好的代码注释能够传达上下文关系和代码目的。不要简单地重申组件或 class 名称。

对于较长的注释，务必书写完整的句子；对于一般性注解，可以书写简洁的短语。
```css
    /* Bad example */
    /* Modal header */
    .modal-header {
    ...
    }

    /* Good example */
    /* Wrapping element for .modal-title and .modal-close */
    .modal-header {
    ...
    }
```

## 连字符CSS选择器命名
* class 名称中只能出现小写字符和破折号（dashe）（不是下划线，也不是驼峰命名法）。破折号应当用于相关 class 的命名（类似于命名空间）（例如，.btn 和 .btn-danger）。
* 避免过度任意的简写。.btn 代表 button，但是 .s 不能表达任何意思
* class 名称应当尽可能短，并且意义明确。
* 使用有意义的名称。使用有组织的或目的明确的名称，不要使用表现形式（presentational）的名称。
* 基于最近的父 class 或基本（base） class 作为新 class 的前缀。
* 使用 .js-* class 来标识行为（与样式相对），并且不要将这些 class 包含到 CSS 文件中。
* 尽量不要用使用id
* 长名称或词组可以使用中'-'为选择器命名，不建议使用'_'下划线来命名CSS选择器
输入时候可以少按一个shift键，浏览器兼容性问题(比如使用_tips的选择器命名，在IE6是无效的)
能良好区分javaScript变量命名（JS变量命名是用'_'）
```css
    /* Bad example */
    .t { ... }
    .red { ... }
    .header { ... }

    /* Good example */
    .tweet { ... }
    .important { ... }
    .tweet-header { ... }
```
## 精简高效CSS命名之"三无原则"
* NO ID！ 
```css
/* Bad example */
    #test { ... }
```
* NO 辈分层级！
```css
/* Bad example */
    .test span { ... }
```
* NO 标签！
```css
/* Bad example */
    li.test { ... }
```
CSS命名就应该最简单、最直接，直捣黄龙。没有HTML标签，没有层级。为什么不要？
* 限制重用

我们会使用层级(#test .test)，会使用标签(ul.test)，可能是习惯(没多想)，或是为了避免冲突。但是你限制越多，越抑制CSS的重用性
* CSS文件大小  

如果你的css名称层级多，字符长。随着一个项目的发展，样式文件大小会比精简css的名称大的多
* 降低了渲染效率  

举个栗子
```html
 <div id="test">
    <ul class="test"></ul>
 </div>
```
现在要给这里的ul标签一个样式，比如说padding-left:25px;那么下面四种写法哪个渲染速度最快？
```css
  #test .test{}， ul.test{}，#test ul{} 以及.test{}
```
如果单纯的ul与.test PK，我还真拿不定谁的渲染速度更快些。但是，一旦牵扯到层级与标签，我100%确定，.test这种最直接的命名方式渲染效率是最高的  
在《高性能网站进阶指南》一书曾提到CSS的渲染方式是“从右往左”渲染的。也就是说先渲染最右的元素之后再找它老爹。  
CSS命名，只要出现了层级，出现了标签，就是一次额外的渲染，层级越多，渲染的开销也就越大
* 但也不是绝对没有，只是尽可能的少
"无ID"其实与性能没多大关系，只是一般id与JavaScript有奸情  
## 选择器
* 对于通用元素使用 class ，这样利于渲染性能的优化。
* 对于经常出现的组件，避免使用属性选择器（例如，[class^="..."]）。浏览器的性能会受到这些因素的影响。
* 选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 3 。
* 只有在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时 -- 前缀类似于命名空间）。
```css
    /* Bad example */
    span { ... }
    .page-container #stream .stream-item .tweet .tweet-header .username { ... }
    .avatar { ... }

    /* Good example */
    .avatar { ... }
    .tweet-header .username { ... }
    .tweet .avatar { ... }
```

## 代码组织
* 以组件为单位组织代码段。
* 制定一致的注释规范
* 使用一致的空白符将代码分隔成块，这样利于扫描较大的文档。
* 如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动。

```css
    /*
    * Component section heading
    */

    .element { ... }


    /*
    * Component section heading
    *
    * Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
    */

    .element { ... }

    /* Contextual sub-component or modifer */
    .element-heading { ... }
```

# 关于 Interoperable CSS
https://glenmaddern.com/articles/interoperable-css

* css  

```css
    /* nav.scss */
    :export {
    Nav: _nav_nav_afd97dfs867;
    Logo: _nav_logo_97fd867fsfg;
    }
    ._nav_nav_afd97dfs867 { /* nav styles */ }
    ._nav_logo_97fd867fsfg { /* logo styles */ }
```

* Component 
```javascript  

    import styles from './nav.scss'
    ...
    render() {
        return (
            <div className={styles.Nav}>
                <div className={styles.Logo}></div>
            </div>
        )
    }
    
```