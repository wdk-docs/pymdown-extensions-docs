# 常见问题

## YAML 中的功能参考

> 如果我使用的模块[MkDocs][mkdocs]?

Pymdown 扩展程序具有许多扩展，可以通过获取功能引用的选项来揭示自定义。
如果您使用的是[MkDocs][mkdocs]之类的项目，该项目允许用户通过 YAML 配置 Python Markdown 扩展，则指定功能引用可能不会直观。

请记住，以下示例专门参考通过
[PyYAML][pyyaml]并配置为允许 Python 对象。

指定 PyYAML 中的函数参考, 您必须使用`#!yaml !!python/name:`预处理功能 .
如果要使用参数配置函数 -- 就像我们需要`slugs.slugify` or `arithmatex`'s 的 SuperFence 的自定义围栏 -- 那你必须使用 `#!yaml !!python/object/apply:`.
例如，为了指定 Python Markdown 的 TOC 扩展名以使用 Markdown 中的 Pymdown 扩展名之一，我们将使用该格式，以便我们可以指定关键字参数。

```yaml
markdown_extensions:
  - markdown.extensions.toc:
      slugify: !!python/object/apply:pymdownx.slugs.slugify { kwds: { case: lower } }
      permalink: "\ue157"
```

要在表情符号扩展中指定特定的表情符号生成器，这只需要一个简单的函数参考：

```yaml
markdown_extensions:
  - pymdownx.emoji:
      emoji_generator: !!python/name:pymdownx.emoji.to_png
```

## GitHub-ish 配置

> How do I get GitHub Flavored Markdown?

A recommended GitHub configuration is provided below to emulate a setup that gives a GitHub feel.

For GitHub issue, commit, pull request, and mention shorthand syntax, you will also need to specify a `provider`, `user`
and `repo` in MagicLink's options below. This gives relative context for shorthand links (like `#1`) so that links can
properly be generated. In the example below, we will use `facelessuser` and `pymdown-extensions` as the user and
repository respectively. See [MagicLink](./extensions/magiclink.md) for more details.

!!! tip
If you are attempting to configure these options in a YAML based configuration (like in [MkDocs][mkdocs]), please
see the related [FAQ question](#function-references-in-yaml) to see how to specify function references in YAML.

```py3
from pymdownx import emoji

extensions = [
    'markdown.extensions.tables',
    'pymdownx.magiclink',
    'pymdownx.betterem',
    'pymdownx.tilde',
    'pymdownx.emoji',
    'pymdownx.tasklist',
    'pymdownx.superfences',
    'pymdownx.saneheaders'
]

extension_configs = {
    "pymdownx.magiclink": {
        "repo_url_shortener": True,
        "repo_url_shorthand": True,
        "provider": "github",
        "user": "facelessuser",
        "repo": "pymdown-extensions"
    },
    "pymdownx.tilde": {
        "subscript": False
    },
    "pymdownx.emoji": {
        "emoji_index": emoji.gemoji,
        "emoji_generator": emoji.to_png,
        "alt": "short",
        "options": {
            "attributes": {
                "align": "absmiddle",
                "height": "20px",
                "width": "20px"
            },
            "image_path": "https://assets-cdn.github.com/images/icons/emoji/unicode/",
            "non_standard_image_path": "https://assets-cdn.github.com/images/icons/emoji/"
        }
    }
}
```

## 美人鱼图

The short answer is to use [SuperFences' custom fence feature](./extensions/superfences.md#custom-fences). We provide
a basic [example using SuperFences](./extensions/superfences.md#uml-diagram-example), but in order to get a really
solid Mermaid experience, we actually go a bit further in our documents. While we don't often have time to answer
everyone's questions regarding Mermaid, we have provided some fairly extensive notes on how we achieved Mermaid diagrams
in this documents. Check out the notes [here](./extras/mermaid.md).

## Arithmatex 通用模式在 MkDocs 中不起作用

This question comes up every now and as there are a number of people that like to use Arithmatex in the MkDocs
environment. For whatever reason, people often gravitate towards the "generic" mode over the "default" mode. And
inevitably, we'll get an issue regarding why math rendering isn't working with Arithmatex in MkDocs.

If you are affected by this issue, the first question you should ask yourself is whether you are using the
[`mkdocs-minify-plugin`](https://github.com/byrnereese/mkdocs-minify-plugin). If you are using this plugin, you must
either discontinue using it (which is not usually the desired approach) or use Arithmatex's "default" mode and MathJax
configuration as outlined in its [documentation](./extensions/arithmatex.md#loading-mathjax).
