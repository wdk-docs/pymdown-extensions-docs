[:octicons-file-code-24:][_slugs]{: .source-link }

# Slugs - 蛞蝓

## 交替Slugify

Python Markdown的默认惰性用于删除所有Unicode字符。
虽然这不再是必然的，PyMdown Extensions提供了一个可配置的slugify来帮助那些有选择器首选项的人。
这些都是非常简单的惰性选项。
有很多选择，其中一些非常复杂。
有些人可能更喜欢使用其中一种，但如果您只想要简单的东西，这可能会满足要求。

## 使用Slugify

`slugify` 是一个简单的Unicode slugify选项。
它使用各种参数来控制在slugs中如何执行大小写，首选哪种Unicode规范化，以及是否首选Unicode的百分比编码。

可用的关键字选项如下:

| Parameter        | Default        | Description                                                  |
| ---------------- | -------------- | ------------------------------------------------------------ |
| `case`           | `#!py3 'none'` | 字符的控制大小写规范化。请参阅下面的大小写选项。             |
| `percent_encode` | `#!py3 False`  | %在大小写规范化后对所有Unicode字符进行编码。                 |
| `normalize`      | `#!py3 'NFC'`  | Unicode规范化方法。例如，`NFD`会去掉变音符号，但 `NFC`不会。 |

案例选项描述如下:

| Option        | Description                                                                             |
| ------------- | --------------------------------------------------------------------------------------- |
| `none`        | Performs no case normalization preserving whatever case is provided.                    |
| `lower`       | Performs simple lower casing on the slug which will operate on Unicode and ASCII alike. |
| `lower-ascii` | Performs simple lower casing on only ASCII upper case characters.                       |
| `fold`        | Applies Python's case folding function on the slug.                                     |

配置是直接的。只需导入段塞模块并配置您希望Toc扩展如何利用段塞。

```py
extension = ['markdown.extensions.toc']
extension_configs = {
    'markdown.extensions.toc': {
        "slugify": slugs.slugify(case="lower", percent_encode=True)
    }
}
```

如果你正在使用像[MkDocs][MkDocs]这样的东西，请查看我们的[FAQ](../faq.md#function-references-in-yaml)，它提供了如何在YAML配置中指定可配置函数的指导。
