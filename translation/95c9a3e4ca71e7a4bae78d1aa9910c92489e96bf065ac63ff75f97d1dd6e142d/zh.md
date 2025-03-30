```
define_editor(fn, pattern; wait=false)
```

定义一个新的编辑器，匹配 `pattern`，可以使用 `fn` 打开一个文件（可能在给定的行号处）。

`fn` 参数是一个函数，用于确定如何使用给定的编辑器打开文件。它应该接受四个参数，如下所示：

  * `cmd` - 编辑器的基本命令对象
  * `path` - 要打开的源文件的路径
  * `line` - 要在其处打开编辑器的行号
  * `column` - 要在其处打开编辑器的列号

无法通过命令打开特定行或特定列的编辑器可以忽略 `line` 和/或 `column` 参数。`fn` 回调必须返回一个适当的 `Cmd` 对象以打开文件，或者返回 `nothing` 表示它们无法编辑此文件。使用 `nothing` 表示该编辑器不适合当前环境，应该尝试另一个编辑器。可以通过直接将回调推送到向量 `EDITOR_CALLBACKS` 来添加更通用的编辑钩子，而不需要生成外部命令。

`pattern` 参数是一个字符串、正则表达式或字符串和正则表达式的数组。为了调用 `fn`，必须有一个模式与 `EDITOR`、`VISUAL` 或 `JULIA_EDITOR` 的值匹配。对于字符串，该字符串必须等于编辑器命令的第一个单词的 [`basename`](@ref)，并去掉其扩展名（如果有的话）。例如，“vi”不匹配“vim -g”，但匹配“/usr/bin/vi -m”；它也匹配 `vi.exe`。如果 `pattern` 是正则表达式，则它与所有编辑器命令作为 shell 转义字符串进行匹配。数组模式如果其任何项匹配则匹配。如果多个编辑器匹配，则使用最近添加的那个。

默认情况下，julia 不会等待编辑器关闭，而是在后台运行它。然而，如果编辑器是基于终端的，您可能希望设置 `wait=true`，julia 将在恢复之前等待编辑器关闭。

如果设置了其中一个编辑器环境变量，但没有编辑器条目与之匹配，则调用默认编辑器条目：

```
(cmd, path, line, column) -> `$cmd $path`
```

请注意，许多编辑器已经定义。以下所有命令应该已经可以工作：

  * emacs
  * emacsclient
  * vim
  * nvim
  * nano
  * micro
  * kak
  * helix
  * textmate
  * mate
  * kate
  * subl
  * atom
  * notepad++
  * Visual Studio Code
  * open
  * pycharm
  * bbedit

# 示例

以下定义了基于终端的 `emacs` 的用法：

```
define_editor(
    r"\bemacs\b.*\s(-nw|--no-window-system)\b", wait=true) do cmd, path, line
    `$cmd +$line $path`
end
```

!!! compat "Julia 1.4"
    `define_editor` 是在 Julia 1.4 中引入的。

