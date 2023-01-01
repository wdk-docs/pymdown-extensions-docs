[:octicons-file-code-24:][_pathconverter]{: .source-link }

# PathConverter

## Overview

PathConverter 是一个扩展程序，可以将局部，相对参考路径转换为链接和图像的绝对或相对路径。
它最初是为想要通过在临时位置渲染的项目而为一个项目编写的。
该扩展使路径可以转换为从临时位置工作。
当试图理解为什么创建此扩展名时，此上下文很重要。
实际用法仅限于这样的情况，因此在大多数普通情况下都不会使用它。

PathConverter 采用绝对基本路径。
基本路径是转换时降价内容的假设位置。
该路径用作定位图像和引用文件相对于 Markdown 内容的参考。
从本质上讲，在转换时间，Markdown 文件中的引用相对于此基本路径。
参考的存在未得到验证，但是进行了分析以确定它是否是相对路径，如果是，则有资格进行转换。
在 **绝对** 模式的情况下，相对标记引用将转换为绝对路径。

If PathConverter is in **relative** mode, the extension will also need a relative path to convert to. The relative path
must be an absolute path to the location the HTML is assumed to live after conversion. If the references paths can be
confirmed to be relative, those references will be converted to relative paths that align to the provided relative path
parameter. The idea is that a Markdown file could be found in a location that is not meant to be its final location.
References within the Markdown source would link relative to the base path, but they would then be converted to be
relative to it's new location -- the relative path parameter.

Currently PathConverter will search desired tags for `href` and `src` attributes. By default, only `a`, `script`, `img`,
and `link` tags are searched.

PathConverter is also intelligent enough to only operate on the file portion of the reference link. Consider the
following scenario: `path/to/file.html#header-to-jump-to`. In the example, `path/to/file.html` will be converted, but
`#header-to-jump-to` will be left unaltered.

As mentioned before, the use cases for something like this are limited, but if you have a situation that lends well to
something like this, PathConverter can help.

The PathConverter extension can be included in Python Markdown by using the following:

```py3
import markdown
md = markdown.Markdown(extensions=['pymdownx.pathconverter'])
```

## Options

| Option          | Type   | Default                     | Description                                                                                                              |
| --------------- | ------ | --------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| `base_path`     | string | `#!py3 ''`                  | A string indicating an absolute base path to be used to find referenced files.                                           |
| `relative_path` | string | `#!py3 ''`                  | A string indicating an absolute path that the references are to be relative to (not used when `absolute` is set `True`). |
| `absolute`      | bool   | `#!py3 False`               | Determines whether paths are converted to absolute or relative.                                                          |
| `tags`          | string | `#!py3 'a script img link'` | Tags (separated by spaces) that are searched to find `href` and `src` attributes.                                        |
| `file_scheme`   | bool   | `#!py3 False`               | Produce file:// URLs instead of raw paths when converting paths to absolute.                                             |
