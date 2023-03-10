[:octicons-file-code-24:][_striphtml]{: .source-link }

# StripHTML

## Overview

StripHTML(正式名称为 PlainHTML)是一个简单的扩展，在后期处理结束时运行。  
它搜索最终输出，去掉不需要的注释和/或标记属性。
虽然它尽量在进程的最后加载，但在加载扩展时将它包含在最后会有所帮助。

!!! example "Strip Comment"

    === "HTML"
        ```html
        <p>Here is a <strong>test</strong>.</p>
        ```

    === "Markdown"
        ```
        <!-- We are only allowing strip_comments and strip_js_on_attributes
             in this example. -->

        Here is a <strong onclick="myFunction();">test</strong>.
        ```

Because comments aren't stripped until the end in a post-processing step, they are present throughout the entire
Markdown conversion process and could possibly affect parsing, so be careful how you generally insert comments.

!!! caution "Warning"
This is not meant to be a sanitizer for HTML. This is just meant to try and strip out style, script, classes, etc.
to provide a plain HTML output for the times this is desired; this is not meant as a security extension. If you
want something to secure the output, you should consider running a sanitizer like [Bleach][bleach].

The StripHTML extension can be included in Python Markdown by using the following:

```py3
import markdown
md = markdown.Markdown(extensions=['pymdownx.striphtml'])
```

## Options

By default, StripHTML strips the following attributes: `style`, `id`, `class`, and `on<name>`. StripHTML also strips
HTML comments. If desired, its behavior can be configured to strip less or even more, but it is limited to attributes
and comments.

| Option                   | Type     | Default      | Description                                                                   |
| ------------------------ | -------- | ------------ | ----------------------------------------------------------------------------- |
| `strip_comments`         | bool     | `#!py3 True` | Strip HTML comments during post process.                                      |
| `strip_js_on_attributes` | bool     | `#!py3 True` | Strip JavaScript script attributes with the pattern on\* during post process. |
| `strip_attributes`       | [string] | `#!py3 []`   | A list of tag attribute names to strip.                                       |
