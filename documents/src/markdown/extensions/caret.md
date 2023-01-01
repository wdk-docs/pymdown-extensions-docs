[:octicons-file-code-24:][_caret]{: .source-link }

# Caret

## Overview

Caret 可选地添加两个不同的功能，这些功能是围绕角色`^`构建的。
The first is **insert** which inserts `#!html <ins></ins>` tags.
The second is **superscript** which inserts `#!html <sup></sup>` tags.

可以通过以下内容包含在 Python Markdown 中的 Caret 扩展名：

```py3
import markdown
md = markdown.Markdown(extensions=['pymdownx.caret'])
```

## Insert

To wrap content in an **insert** tag, simply surround the text with double `^`.
You can also enable `smart_insert` in the [options](#options).
Smart behavior of **insert** models that of [BetterEm](betterem.md#differences).

!!! example "Insert Example"

    === "Output"
        ^^Insert me^^

    === "Markdown"
        ```
        ^^Insert me^^
        ```

## Superscript

To denote a superscript, you can surround the desired content in single `^`. It uses Pandoc style logic, so if your
superscript needs to have spaces, you must escape the spaces.

!!! example "Superscript Example"

    === "Output"
        H^2^0

        text^a\ superscript^

    === "Markdown"
        ```
        H^2^0

        text^a\ superscript^
        ```

## Options

| Option         | Type | Default      | Description                             |
| -------------- | ---- | ------------ | --------------------------------------- |
| `smart_insert` | bool | `#!py3 True` | Use smart logic with insert characters. |
| `insert`       | bool | `#!py3 True` | Enable insert feature.                  |
| `superscript`  | bool | `#!py3 True` | Enable superscript feature.             |
