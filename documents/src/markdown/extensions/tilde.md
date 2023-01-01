[:octicons-file-code-24:][_tilde]{: .source-link }

# Tilde

## Overview

波浪号可选地添加了两个不同的特征，这些特征在语法上围绕`~`字符构建: **delete** 插入 `#!html <del></del>` 标记和**subscript** 插入 `#!html <sub></sub>` 标记.

波浪号扩展可以通过以下方式包含在 Python Markdown 中:

```py3
import markdown
md = markdown.Markdown(extensions=['pymdownx.tilde'])
```

## Delete

要将内容包装在 **delete** 标记中，只需用两个 `~` 将文本环绕起来。
您也可以在[选项](#options)中启用 `smart_delete` .
智能 **删除** 行为的模型[BetterEm](betterem.md#differences).

!!! example "Delete Example"

    === "Output"
        ~~Delete me~~

    === "Markdown"
        ```
        ~~Delete me~~
        ```

## Subscript

To denote a subscript, you can surround the desired content in single `~`. It uses Pandoc style logic, so if your
subscript needs to have spaces, you must escape the spaces.

!!! example "Subscript Example"

    === "Output"
        CH~3~CH~2~OH

        text~a\ subscript~

    === "Markdown"
        ```
        CH~3~CH~2~OH

        text~a\ subscript~
        ```

## Options

| Option         | Type | Default      | Description                             |
| -------------- | ---- | ------------ | --------------------------------------- |
| `smart_delete` | bool | `#!py3 True` | Use smart logic with delete characters. |
| `delete`       | bool | `#!py3 True` | Enable delete feature.                  |
| `subscript`    | bool | `#!py3 True` | Enable subscript feature.               |
