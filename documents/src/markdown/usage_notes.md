# 使用笔记

## 不兼容的扩展

PyMdown Extensions包括三个扩展，用来 **替换** 默认Python Markdown扩展中的对应扩展。
你不必使用PyMdown Extensions的所有扩展，但如果你选择使用下面的一个包，你应该使用它而不是Python Markdown; **它们不能同时加载**。

此外，您不应该包含一个扩展超过一次。
如果您试图同时包含多个扩展，您可能会得到意想不到的结果。
另外，要注意一些扩展是包含多个扩展的便利扩展;注意它们包含的内容，这样您就不会意外地单独重新包含它们。

- `pymdownx.superfences` 替换 `markdown.extensions.fenced_code`.

- `pymdownx.betterem` 替换 `markdown.extensions.smartstrong`.

- `pymdownx.extra` 替换 `markdown.extensions.extra`, 但是记住, `pymdown.extra` 是一个方便的扩展，只是一个包装器，包括许多扩展。 记住要避免包括这个，然后包括冲突的扩展或扩展的双重。以下是包含的扩展的完整列表:

    ```
    pymdownx.betterem
    pymdownx.superfences
    markdown.extensions.footnotes
    markdown.extensions.attr_list
    markdown.extensions.def_list
    markdown.extensions.tables
    markdown.extensions.abbr
    markdown.extensions.md_in_html
    ```
