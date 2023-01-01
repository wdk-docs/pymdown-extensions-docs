[:octicons-file-code-24:][_saneheaders]{: .source-link }

# SaneHeaders

## Overview

SaneHeaders 是一个扩展，它改变了默认的散列头扩展，要求头在散列后有空格(`#`)，以便被识别为头。
这允许其他扩展语法在它们的语法中使用`#`，只要行首的`#`后面没有空格。
For instance,[MagicLink's issue syntax](./magiclink.md#issues-and-pull-requests) issue syntax uses hashes followed by numbers (`#998`) to represent issue links. There may extensions that use names after hashes to provide tags (`#tag`).
With SaneHeaders, these syntaxes can coexist. Those familiar with CommonMark may recognize this behavior.

```py3
import markdown
md = markdown.Markdown(extensions=['pymdownx.saneheaders'])
```

## Syntax

The syntax when using SaneHeaders is exactly like Python Markdown's default logic with the only exception being that
SaneHeaders will not treat hashes at the beginning of a line as a header if they do not have space after them.

In Python Markdown, both of these are treated as headers:

```
## Header

##Also a Header
```

With SaneHeaders, only the first is a header:

```
## Header

##Not a Header
```
