# 安装

## 需求

为了使PyMdown 扩展工作，有几个先决条件。

| 名字                               | 必须 | 描述                                                                                                                   |
| ---------------------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------- |
| [Python Markdown][python-markdown] | Yes  | Python Markdown必须安装，因为它是正在使用的Markdown解析器。                                                            |
| [Pygments (optional)][pygments]    | No   | 如果Pygments需要语法高亮显示，则必须安装Pygments。这可以省略，代码块将被格式化，以便与JavaScript代码高亮显示一起使用。 |

## 安装

使用pip易于安装:

```console
$ pip install pymdown-extensions
```

如果你想手动安装，运行:

```console
$ python setup.py build
$ python setup.py install
```

安装后，您应该能够在Python Markdown的命名空间下访问扩展 `pymdownx.<extension>`.

如果你想修改代码，可以通过以下方式安装:

```console
$ pip install --editable .
```

此方法将允许您立即看到更改，而无需重新安装。
如果您想在虚拟机中执行此操作，您可以这样做。