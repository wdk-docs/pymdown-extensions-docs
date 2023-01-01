[:octicons-file-code-24:][_mark]{: .source-link }

# Mark

## Overview

Mark 添加了插入`#!html <mark></mark>`标签的能力。  
语法要求文本被双重符号包围。
可以选择将其配置为使用智能逻辑。**mark** 模型的智能和非智能变体的语法行为[BetterEm](betterem.md#differences).

要标记一些文本，只需用双`=`包围文本。

!!! example "Mark Example"

    === "Output"
        ==mark me==

        ==smart==mark==

    === "Markdown"
        ```
        ==mark me==

        ==smart==mark==
        ```

通过以下内容，可以将标记扩展名包含在Python Markdown中：

```py3
import markdown
md = markdown.Markdown(extensions=['pymdownx.mark'])
```

## 选项

| 选项       | Type | Default      | Description                           |
| ------------ | ---- | ------------ | ------------------------------------- |
| `smart_mark` | bool | `#!py3 True` | Use smart logic with mark characters. |
