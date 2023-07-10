# PyMdown 扩展

## 概述

PyMdown Extensions是Python Markdown的扩展集合。
最初编写它们是为了使编写文档更愉快。
它们涵盖了广泛的解决方案，虽然不是所有人都需要每个扩展，但通常至少有一个对每个人都有用的扩展。

## 使用

所有扩展都在`pymdownx`的模块命名空间下找到。
假设我们想要指定MagicLink扩展的使用，我们将在Python Markdown中包含它，如下所示:

```pycon3
>>> import markdown
>>> text = "A link https://google.com"
>>> html = markdown.markdown(text, extensions=['pymdownx.magiclink'])
'<p>A link <a href="https://google.com">https://google.com</a></p>'
```

查看每个扩展的文档，以了解有关如何配置和使用每个扩展的更多信息。

!!! danger "Reminder"
    
    请阅读[用法说明](usage_notes.md)获取有关扩展兼容性的信息以及使用这些扩展时要注意的一般注意事项。

## 扩展

!!! summary "Arithmatex"
    [Arithmatex](extensions/arithmatex.md)是一个扩展，它在Markdown转换过程中保留LaTeX数学方程($\frac{\sqrt x}{y^3}$)，以便它们可以与[MathJax][MathJax]一起使用。

!!! summary "B64 - Base64"
    [B64](extensions/b64.md)将文档中的所有本地图像转换为base64编码并嵌入到文档中。

!!! summary "BetterEm"
    [BetterEm](extensions/betterem.md)是一种不同于Python Markdown默认的**强调**方法。
    它的工作原理类似，但处理某些极端情况的方式不同。

!!! summary "Caret - 脱字符号"
    [Caret](extensions/caret.md)是一个语法上围绕`^`字符构建的扩展。
    它增加了对插入 超级^脚本^ 的支持，并添加了一种简单的方法来将 ^^文本^^ 放在`#! html `标签。

!!! summary "Critic"
    [Critic](extensions/critic.md)增加了对[Critic Markup][critic-markup]的处理和支持。

!!! summary "Details"
    [Details](extensions/details.md) 创建带有 `#!html <details><summary>` 标签的可折叠元素.

    ??? note "Click Me!"
        Thanks!

!!! summary "Emoji"
    [Emoji](extensions/emoji.md) 通过Markdown添加表情符号很容易 :smile:.

!!! summary "EscapeAll"
    [EscapeAll](extensions/escapeall.md) 允许转义任何字符，其中一些具有附加效果。 点击这里了解更多。

!!! summary "Extra"
    [Extra](extensions/extra.md) 就像Python Markdown的Extra包，除了它使用PyMdown扩展来替代类似的扩展。

!!! summary "Highlight"
    [Highlight](extensions/highlight.md) 允许您配置[SuperFences](extensions/superfences.md) 和 [InlineHilite](extensions/inlinehilite.md)的语法高亮显示. 还通过语法高亮器传递标准Markdown缩进代码块。  

!!! summary "InlineHilite"
    [InlineHilite](extensions/inlinehilite.md) 突出显示内联代码: `#!py3 from module import function as func`.

!!! summary "Keys"
    [Keys](extensions/keys.md) 使在文档中插入关键输入就像按 ++ctrl+alt+delete++ 键一样简单.

!!! summary "MagicLink"
    [MagicLink](extensions/magiclink.md) 它可以链接URL和电子邮件链接，而不必用Markdown语法包装它们。
    此外，它还为流行的代码托管提供商自动缩短了存储库发布、拉取请求和提交链接。
    您甚至可以使用特殊的速记语法来链接问题、差异，甚至提到人

!!! summary "Mark"
    [Mark](extensions/mark.md) 允许您轻松地 ==标记== 单词。

!!! summary "PathConverter"
    [PathConverter](extensions/pathconverter.md) 将路径转换为给定基本路径的绝对路径或相对路径。

!!! summary "ProgressBar"
    [ProgressBar](extensions/progressbar.md) 创建进度条快速和容易。

    [== 80%]{: .candystripe .candystripe-animate}

!!! summary "SaneHeaders"
    [SaneHeaders](extensions/saneheaders.md) 将哈希头修改为仅在开始哈希符号后面至少有一个空格时才计算。
    如果您使用其他也使用哈希符号的扩展(如我们自己的MagicLink扩展)，这是有用的。

!!! summary "SmartSymbols"
    [SmartSymbols](extensions/smartsymbols.md) 通过简单的ASCII表示插入常用的Unicode字符: `=/=` -->  =/=.

!!! summary "Snippets"
    [Snippets](extensions/snippets.md) 将其他Markdown或HTML片段包含到当前正在解析的Markdown文件中。

!!! summary "StripHTML"
    [StripHTML](extensions/striphtml.md) 可以去掉HTML注释和特定的标记属性。

!!! summary "SuperFences"
    [SuperFences](extensions/superfences.md) 就像Python Markdown的栅栏，但更好。
    在列表、警告和其他语法下嵌套栅栏。
    您甚至可以为UML之类的内容创建特殊的自定义栅栏。

    === "Output"

        ```diagram
        graph TB
            c1-->a2
            subgraph one
            a1-->a2
            end
            subgraph two
            b1-->b2
            end
            subgraph three
            c1-->c2
            end
        ```

    === "Markdown"

        ````
        ```diagram
        graph TB
            c1-->a2
            subgraph one
            a1-->a2
            end
            subgraph two
            b1-->b2
            end
            subgraph three
            c1-->c2
            end
        ```
        ````

!!! summary "Tabbed"
    [Tabbed](extensions/tabbed.md) 允许标签式Markdown内容:

    === "Tab 1"
        Markdown **content**.

    === "Tab 2"
        More Markdown **content**.

!!! summary "Tasklist"
    [Tasklist](extensions/tasklist.md) 允许插入带有复选框的列表。

    - [x] eggs
    - [x] bread
    - [ ] milk

!!! summary "Tilde"
    [Tilde](extensions/tilde.md) 语法上是围绕`~`字符构建的吗. 
    它增加了对插入子脚本的支持，并添加了一种简单的方法来将文本放入`#!html <del>`标签。
