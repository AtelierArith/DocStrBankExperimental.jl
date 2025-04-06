```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/REPL/docs/src/index.md"
```

# The Julia REPL

Julia 附带一个功能齐全的交互式命令行 REPL（读取-评估-打印循环），内置于 `julia` 可执行文件中。除了允许快速和轻松地评估 Julia 语句外，它还具有可搜索的历史记录、标签补全、许多有用的键绑定以及专用的帮助和 shell 模式。可以通过简单地调用 `julia` 而不带任何参数或双击可执行文件来启动 REPL：

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia>\n```")
```

要退出交互式会话，请在空白行上输入 `^D` – 控制键与 `d` 键一起按下 – 或输入 `exit()` 然后按回车键。REPL 会以横幅和 `julia>` 提示符欢迎您。

## The different prompt modes

### The Julian mode

REPL 有五种主要的操作模式。第一种也是最常见的是朱利安提示符。它是默认的操作模式；每一行最初以 `julia>` 开头。在这里，您可以输入 Julia 表达式。在输入完整的表达式后按回车或输入将会评估该条目并显示最后一个表达式的结果。

```jldoctest
julia> string(1 + 2)
"3"
```

有许多独特于交互式工作的有用功能。除了显示结果，REPL 还将结果绑定到变量 `ans`。行末的分号可以用作标志，以抑制结果的显示。

```jldoctest
julia> string(3 * 4);

julia> ans
"12"
```

在 Julia 模式下，REPL 支持一种称为 *提示粘贴* 的功能。当粘贴以 `julia>` 开头的文本到 REPL 时，这个功能会被激活。在这种情况下，只有以 `julia>` 开头的表达式（以及其他 REPL 模式提示：`shell>`、`help?>`、`pkg>`）会被解析，而其他的则会被移除。这使得可以粘贴从 REPL 会话中复制的一段文本，而无需清除提示和输出。此功能默认启用，但可以通过 `REPL.enable_promptpaste(::Bool)` 随意禁用或启用。如果启用，您可以通过将上段代码块直接粘贴到 REPL 中来尝试此功能。由于标准 Windows 命令提示符在检测粘贴发生时的限制，此功能在其上无法使用。

Objects are printed at the REPL using the [`show`](@ref) function with a specific [`IOContext`](@ref). In particular, the `:limit` attribute is set to `true`. Other attributes can receive in certain `show` methods a default value if it's not already set, like `:compact`. It's possible, as an experimental feature, to specify the attributes used by the REPL via the `Base.active_repl.options.iocontext` dictionary (associating values to attributes). For example:

```julia-repl
julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.8833    0.329197
 0.719708  0.59114

julia> show(IOContext(stdout, :compact => false), "text/plain", rand(2, 2))
 0.43540323669187075  0.15759787870609387
 0.2540832269192739   0.4597637838786053
julia> Base.active_repl.options.iocontext[:compact] = false;

julia> rand(2, 2)
2×2 Array{Float64,2}:
 0.2083967319174056  0.13330606013126012
 0.6244375177790158  0.9777957560761545
```

为了在启动时自动定义该字典的值，可以在 `~/.julia/config/startup.jl` 文件中使用 [`atreplinit`](@ref) 函数，例如：

```julia
atreplinit() do repl
    repl.options.iocontext[:compact] = false
end
```

### Help mode

当光标位于行首时，可以通过输入 `?` 将提示符更改为帮助模式。Julia 将尝试打印帮助或文档，适用于在帮助模式下输入的任何内容：

```julia-repl
julia> ? # upon typing ?, the prompt changes (in place) to: help?>

help?> string
search: string String Cstring Cwstring RevString randstring bytestring SubString

  string(xs...)

  Create a string from any values using the print function.
```

宏、类型和变量也可以被查询：

```
help?> @time
  @time

  A macro to execute an expression, printing the time it took to execute, the number of allocations,
  and the total number of bytes its execution caused to be allocated, before returning the value of the
  expression.

  See also @timev, @timed, @elapsed, and @allocated.

help?> Int32
search: Int32 UInt32

  Int32 <: Signed

  32-bit signed integer type.
```

一个字符串或正则表达式字面量使用 [`apropos`](@ref) 搜索所有文档字符串：

```
help?> "aprop"
REPL.stripmd
Base.Docs.apropos

help?> r"ap..p"
Base.:∘
Base.shell_escape_posixly
Distributed.CachingPool
REPL.stripmd
Base.Docs.apropos
```

帮助模式的另一个功能是访问扩展文档字符串。您可以通过输入类似 `??Print` 而不是 `?Print` 的内容来实现，这将显示源代码文档中的 `# 扩展帮助` 部分。

帮助模式可以通过在行首按下退格键退出。

### [Shell mode](@id man-shell-mode)

就像帮助模式对于快速访问文档很有用一样，另一个常见的任务是使用系统 shell 执行系统命令。就像在行首输入 `?` 进入帮助模式一样，分号 (`;`) 将进入 shell 模式。并且可以通过在行首按下退格键来退出。

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> echo hello
hello
```

!!! note
    对于Windows用户，Julia的shell模式不支持Windows shell命令。因此，这将失败：


```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> dir
ERROR: IOError: could not spawn `dir`: no such file or directory (ENOENT)
Stacktrace!
.......
```

然而，您可以通过以下方式访问 `PowerShell`：

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> powershell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.
PS C:\Users\elm>
```

... 并像这样使用 `cmd.exe`（参见 `dir` 命令）：

```julia-repl
julia> ; # upon typing ;, the prompt changes (in place) to: shell>

shell> cmd
Microsoft Windows [version 10.0.17763.973]
(c) 2018 Microsoft Corporation. All rights reserved.
C:\Users\elm>dir
 Volume in drive C has no label
 Volume Serial Number is 1643-0CD7
  Directory of C:\Users\elm

29/01/2020  22:15    <DIR>          .
29/01/2020  22:15    <DIR>          ..
02/02/2020  08:06    <DIR>          .atom
```

### Pkg mode

包管理器模式接受专门的命令来加载和更新包。通过在Julian REPL提示符下按`]`键进入该模式，通过按CTRL-C或在行首按退格键退出。该模式的提示符为`pkg>`。它支持自己的帮助模式，可以通过在`pkg>`提示符的行首按`?`键进入。包管理器模式在Pkg手册中有文档，手册可在[https://julialang.github.io/Pkg.jl/v1/](https://julialang.github.io/Pkg.jl/v1/)找到。

### Search modes

在上述所有模式中，执行的行会保存到历史文件中，可以进行搜索。要启动对先前历史的增量搜索，请输入 `^R` – 控制键与 `r` 键一起按下。提示符将更改为 ```(reverse-i-search)`':```, 当您输入时，搜索查询将出现在引号中。与查询匹配的最新结果将在冒号右侧动态更新，随着输入的增加而变化。要使用相同的查询查找较旧的结果，只需再次输入 `^R`。

就像 `^R` 是反向搜索，`^S` 是正向搜索，提示为 ```(i-search)`':```.  这两者可以结合使用，以分别在之前或之后的匹配结果中移动。

所有在 Julia REPL 中执行的命令都会记录到 `~/.julia/logs/repl_history.jl` 中，连同执行时间戳和您所处的当前 REPL 模式。搜索模式会查询此日志文件，以查找您之前运行的命令。您可以通过在启动时传递 `--history-file=no` 标志来禁用此功能。

## Key bindings

Julia REPL 很好地利用了键绑定。上面已经介绍了几个控制键绑定（`^D` 退出，`^R` 和 `^S` 用于搜索），但还有很多其他的。除了控制键，还有元键绑定。这些在不同平台上有所不同，但大多数终端默认使用按住 alt 或 option 键与其他键一起发送元键（或者可以配置为这样做），或者先按 Esc 然后再按其他键。

| Keybinding           | Description                                                                                                |
|:-------------------- |:---------------------------------------------------------------------------------------------------------- |
| **Program control**  |                                                                                                            |
| `^D`                 | Exit (when buffer is empty)                                                                                |
| `^C`                 | Interrupt or cancel                                                                                        |
| `^L`                 | Clear console screen                                                                                       |
| Return/Enter, `^J`   | New line, executing if it is complete                                                                      |
| meta-Return/Enter    | Insert new line without executing it                                                                       |
| `?` or `;`           | Enter help or shell mode (when at start of a line)                                                         |
| `^R`, `^S`           | Incremental history search, described above                                                                |
| **Cursor movement**  |                                                                                                            |
| Right arrow, `^F`    | Move right one character                                                                                   |
| Left arrow, `^B`     | Move left one character                                                                                    |
| ctrl-Right, `meta-F` | Move right one word                                                                                        |
| ctrl-Left, `meta-B`  | Move left one word                                                                                         |
| Home, `^A`           | Move to beginning of line                                                                                  |
| End, `^E`            | Move to end of line                                                                                        |
| Up arrow, `^P`       | Move up one line (or change to the previous history entry that matches the text before the cursor)         |
| Down arrow, `^N`     | Move down one line (or change to the next history entry that matches the text before the cursor)           |
| Shift-Arrow Key      | Move cursor according to the direction of the Arrow key, while activating the region ("shift selection")   |
| Page-up, `meta-P`    | Change to the previous history entry                                                                       |
| Page-down, `meta-N`  | Change to the next history entry                                                                           |
| `meta-<`             | Change to the first history entry (of the current session if it is before the current position in history) |
| `meta->`             | Change to the last history entry                                                                           |
| `^-Space`            | Set the "mark" in the editing region (and de-activate the region if it's active)                           |
| `^-Space ^-Space`    | Set the "mark" in the editing region and make the region "active", i.e. highlighted                        |
| `^G`                 | De-activate the region (i.e. make it not highlighted)                                                      |
| `^X^X`               | Exchange the current position with the mark                                                                |
| **Editing**          |                                                                                                            |
| Backspace, `^H`      | Delete the previous character, or the whole region when it's active                                        |
| Delete, `^D`         | Forward delete one character (when buffer has text)                                                        |
| meta-Backspace       | Delete the previous word                                                                                   |
| `meta-d`             | Forward delete the next word                                                                               |
| `^W`                 | Delete previous text up to the nearest whitespace                                                          |
| `meta-w`             | Copy the current region in the kill ring                                                                   |
| `meta-W`             | "Kill" the current region, placing the text in the kill ring                                               |
| `^U`                 | "Kill" to beginning of line, placing the text in the kill ring                                             |
| `^K`                 | "Kill" to end of line, placing the text in the kill ring                                                   |
| `^Y`                 | "Yank" insert the text from the kill ring                                                                  |
| `meta-y`             | Replace a previously yanked text with an older entry from the kill ring                                    |
| `^T`                 | Transpose the characters about the cursor                                                                  |
| `meta-Up arrow`      | Transpose current line with line above                                                                     |
| `meta-Down arrow`    | Transpose current line with line below                                                                     |
| `meta-u`             | Change the next word to uppercase                                                                          |
| `meta-c`             | Change the next word to titlecase                                                                          |
| `meta-l`             | Change the next word to lowercase                                                                          |
| `^/`, `^_`           | Undo previous editing action                                                                               |
| `^Q`                 | Write a number in REPL and press `^Q` to open editor at corresponding stackframe or method                 |
| `meta-Left Arrow`    | Indent the current line on the left                                                                        |
| `meta-Right Arrow`   | Indent the current line on the right                                                                       |
| `meta-.`             | Insert last word from previous history entry                                                               |
| `meta-e`             | Edit the current input in an editor                                                                        |

### Customizing keybindings

Julia的REPL键绑定可以通过将字典传递给`REPL.setup_interface`来完全自定义以满足用户的偏好。该字典的键可以是字符或字符串。键`'*'`指的是默认操作。控制加字符`x`的绑定用`"^x"`表示。Meta加`x`可以写成`"\\M-x"`或`"\ex"`，控制加`x`可以写成`"\\C-x"`或`"^x"`。自定义键映射的值必须是`nothing`（表示输入应被忽略）或接受签名`(PromptState, AbstractREPL, Char)`的函数。`REPL.setup_interface`函数必须在REPL初始化之前调用，通过使用[`atreplinit`](@ref)注册操作。例如，要将向上和向下箭头键绑定以在历史记录中移动而不进行前缀搜索，可以将以下代码放入`~/.julia/config/startup.jl`中：

```julia
import REPL
import REPL.LineEdit

const mykeys = Dict{Any,Any}(
    # Up Arrow
    "\e[A" => (s,o...)->(LineEdit.edit_move_up(s) || LineEdit.history_prev(s, LineEdit.mode(s).hist)),
    # Down Arrow
    "\e[B" => (s,o...)->(LineEdit.edit_move_down(s) || LineEdit.history_next(s, LineEdit.mode(s).hist))
)

function customize_keys(repl)
    repl.interface = REPL.setup_interface(repl; extra_repl_keymap = mykeys)
end

atreplinit(customize_keys)
```

用户应参考 `LineEdit.jl` 以了解可用的键输入操作。

## Tab completion

在 REPL 的 Julian、pkg 和 help 模式下，可以输入函数或类型的前几个字符，然后按下 tab 键以获取所有匹配项的列表：

```julia-repl
julia> x[TAB]
julia> xor
```

在某些情况下，它只完成名称的一部分，直到下一个歧义：

```julia-repl
julia> mapf[TAB]
julia> mapfold
```

如果你再次按下 Tab 键，你将获得可能完成此操作的事项列表：

```julia-repl
julia> mapfold[TAB]
mapfoldl mapfoldr
```

当输入行末尾有一个完整的选项补全结果且已输入两个或更多字符时，补全提示将以较浅的颜色显示。可以通过 `Base.active_repl.options.hint_tab_completes = false` 禁用此功能。

!!! compat "Julia 1.11"
    在 Julia 1.11 中添加了 Tab 补全提示功能。


像 REPL 的其他组件一样，搜索是区分大小写的：

```julia-repl
julia> stri[TAB]
stride     strides     string      strip

julia> Stri[TAB]
StridedArray    StridedMatrix    StridedVecOrMat  StridedVector    String
```

制表键还可以用来将 LaTeX 数学符号替换为它们的 Unicode 等价物，并获取 LaTeX 匹配项的列表：

```julia-repl
julia> \pi[TAB]
julia> π
π = 3.1415926535897...

julia> e\_1[TAB] = [1,0]
julia> e₁ = [1,0]
2-element Array{Int64,1}:
 1
 0

julia> e\^1[TAB] = [1 0]
julia> e¹ = [1 0]
1×2 Array{Int64,2}:
 1  0

julia> \sqrt[TAB]2     # √ is equivalent to the sqrt function
julia> √2
1.4142135623730951

julia> \hbar[TAB](h) = h / 2\pi[TAB]
julia> ħ(h) = h / 2π
ħ (generic function with 1 method)

julia> \h[TAB]
\hat              \hermitconjmatrix  \hkswarow          \hrectangle
\hatapprox        \hexagon           \hookleftarrow     \hrectangleblack
\hbar             \hexagonblack      \hookrightarrow    \hslash
\heartsuit        \hksearow          \house             \hspace

julia> α="\alpha[TAB]"   # LaTeX completion also works in strings
julia> α="α"
```

完整的选项卡补全列表可以在手册的 [Unicode Input](@ref) 部分找到。

路径的完成适用于字符串和Julia的Shell模式：

```julia-repl
julia> path="/[TAB]"
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
shell> /[TAB]
.dockerenv  .juliabox/   boot/        etc/         lib/         media/       opt/         root/        sbin/        sys/         usr/
.dockerinit bin/         dev/         home/        lib64/       mnt/         proc/        run/         srv/         tmp/         var/
```

字典键也可以通过制表符完成：

```julia-repl
julia> foo = Dict("qwer1"=>1, "qwer2"=>2, "asdf"=>3)
Dict{String,Int64} with 3 entries:
  "qwer2" => 2
  "asdf"  => 3
  "qwer1" => 1

julia> foo["q[TAB]

"qwer1" "qwer2"
julia> foo["qwer
```

选项卡补全也可以帮助完成字段：

```julia-repl
julia> x = 3 + 4im;

julia> x.[TAB][TAB]
im re

julia> import UUIDs

julia> UUIDs.uuid[TAB][TAB]
uuid1        uuid4         uuid5        uuid_version
```

函数的输出字段也可以被填写：

```julia-repl
julia> split("","")[1].[TAB]
lastindex  offset  string
```

函数输出字段的完成使用类型推断，只有在函数类型稳定时，它才能建议字段。

选项卡补全可以帮助调查与输入参数匹配的可用方法：

```julia-repl
julia> max([TAB] # All methods are displayed, not shown here due to size of the list

julia> max([1, 2], [TAB] # All methods where `Vector{Int}` matches as first argument
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281

julia> max([1, 2], max(1, 2), [TAB] # All methods matching the arguments.
max(x, y) in Base at operators.jl:215
max(a, b, c, xs...) in Base at operators.jl:281
```

关键字也会在建议的方法中显示，在 `;` 之后，见下方 `limit` 和 `keepempty` 是关键字参数的行：

```julia-repl
julia> split("1 1 1", [TAB]
split(str::AbstractString; limit, keepempty) in Base at strings/util.jl:302
split(str::T, splitter; limit, keepempty) where T<:AbstractString in Base at strings/util.jl:277
```

方法的完成使用类型推断，因此即使参数是从函数输出的，也可以查看参数是否匹配。为了使完成能够删除不匹配的方法，函数需要是类型稳定的。

如果您想知道哪些方法可以与特定的参数类型一起使用，请使用 `?` 作为函数名称。这显示了在 InteractiveUtils 中查找接受单个字符串的函数的示例：

```julia-repl
julia> InteractiveUtils.?("somefile")[TAB]
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
```

此列出了可以在字符串上调用的 `InteractiveUtils` 模块中的方法。默认情况下，这排除了所有参数类型为 `Any` 的方法，但您也可以通过按住 SHIFT-TAB 而不是 TAB 来查看这些方法：

```julia-repl
julia> InteractiveUtils.?("somefile")[SHIFT-TAB]
apropos(string) in REPL at REPL/src/docview.jl:796
clipboard(x) in InteractiveUtils at InteractiveUtils/src/clipboard.jl:64
code_llvm(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:221
code_native(f) in InteractiveUtils at InteractiveUtils/src/codeview.jl:243
edit(path::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:197
edit(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:225
eval(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
include(x) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:3
less(file::AbstractString) in InteractiveUtils at InteractiveUtils/src/editless.jl:266
less(f) in InteractiveUtils at InteractiveUtils/src/editless.jl:274
report_bug(kind) in InteractiveUtils at InteractiveUtils/src/InteractiveUtils.jl:391
separate_kwargs(args...; kwargs...) in InteractiveUtils at InteractiveUtils/src/macros.jl:7
```

您还可以使用 `?("somefile")[TAB]` 并查看所有模块，但方法列表可能会很长。

通过省略闭合括号，您可以包含可能需要额外参数的函数：

```julia-repl
julia> using Mmap

help?> Mmap.?("file",[TAB]
Mmap.Anonymous(name::String, readonly::Bool, create::Bool) in Mmap at Mmap/src/Mmap.jl:16
mmap(file::AbstractString) in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}) where T<:Array in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:Array, N} in Mmap at Mmap/src/Mmap.jl:245
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:Array in Mmap at Mmap/src/Mmap.jl:251
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, dims::Tuple{Vararg{Integer, N}}, offset::Integer; grow, shared) where {T<:BitArray, N} in Mmap at Mmap/src/Mmap.jl:316
mmap(file::AbstractString, ::Type{T}, len::Integer) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
mmap(file::AbstractString, ::Type{T}, len::Integer, offset::Integer; grow, shared) where T<:BitArray in Mmap at Mmap/src/Mmap.jl:322
```

## Customizing Colors

Julia 和 REPL 使用的颜色也可以自定义。要更改 Julia 提示符的颜色，您可以将以下内容添加到您的 `~/.julia/config/startup.jl` 文件中，该文件应放置在您的主目录中：

```julia
function customize_colors(repl)
    repl.prompt_color = Base.text_colors[:cyan]
end

atreplinit(customize_colors)
```

可通过在 REPL 的帮助模式中输入 `Base.text_colors` 来查看可用的颜色键。此外，整数 0 到 255 可用作支持 256 种颜色的终端的颜色键。

您还可以通过在上面的 `customize_colors` 函数中设置 `repl` 的相应字段（分别为 `help_color`、`shell_color`、`input_color` 和 `answer_color`）来更改帮助和 shell 提示以及输入和答案文本的颜色。对于后两个，确保 `envcolors` 字段也设置为 false。

也可以通过使用 `Base.text_colors[:bold]` 作为颜色来应用粗体格式。例如，要以粗体字体打印答案，可以在 `~/.julia/config/startup.jl` 中使用以下内容：

```julia
function customize_colors(repl)
    repl.envcolors = false
    repl.answer_color = Base.text_colors[:bold]
end

atreplinit(customize_colors)
```

您还可以通过设置适当的环境变量来自定义用于渲染警告和信息消息的颜色。例如，要分别以洋红色、黄色和青色渲染错误、警告和信息消息，您可以将以下内容添加到您的 `~/.julia/config/startup.jl` 文件中：

```julia
ENV["JULIA_ERROR_COLOR"] = :magenta
ENV["JULIA_WARN_COLOR"] = :yellow
ENV["JULIA_INFO_COLOR"] = :cyan
```

## Changing the contextual module which is active at the REPL

在 REPL 中输入表达式时，它们默认在 `Main` 模块中进行评估；

```julia-repl
julia> @__MODULE__
Main
```

可以通过函数 `REPL.activate(m)` 更改此上下文模块，其中 `m` 是一个 `Module`，或者通过在 REPL 中输入模块并在模块名称上按下键绑定 Alt-m（在 MacOS 上为 Esc-m）。在空提示符上按下键绑定会在之前活动的非 `Main` 模块和 `Main` 之间切换上下文。活动模块会在提示符中显示（除非它是 `Main`）：

```julia-repl
julia> using REPL

julia> REPL.activate(Base)

(Base) julia> @__MODULE__
Base

(Base) julia> using REPL # Need to load REPL into Base module to use it

(Base) julia> REPL.activate(Main)

julia>

julia> Core<Alt-m> # using the keybinding to change module

(Core) julia>

(Core) julia> <Alt-m> # going back to Main via keybinding

julia>

julia> <Alt-m> # going back to previously-active Core via keybinding

(Core) julia>
```

接受可选模块参数的函数通常默认为 REPL 上下文模块。例如，调用 `varinfo()` 将显示当前活动模块的变量：

```julia-repl
julia> module CustomMod
           export var, f
           var = 1
           f(x) = x^2
       end;

julia> REPL.activate(CustomMod)

(Main.CustomMod) julia> varinfo()
  name         size summary
  ––––––––– ––––––– ––––––––––––––––––––––––––––––––––
  CustomMod         Module
  f         0 bytes f (generic function with 1 method)
  var       8 bytes Int64
```

## Numbered prompt

可以获得一个类似于 IPython REPL 和 Mathematica 笔记本的界面，带有编号的输入提示和输出前缀。这可以通过调用 `REPL.numbered_prompt!()` 来实现。如果您希望在启动时启用此功能，请添加

```julia
atreplinit() do repl
    @eval import REPL
    if !isdefined(repl, :interface)
        repl.interface = REPL.setup_interface(repl)
    end
    REPL.numbered_prompt!(repl)
end
```

将其添加到您的 `startup.jl` 文件中。在编号提示中，变量 `Out[n]`（其中 `n` 是一个整数）可用于引用早期的结果：

```julia-repl
In [1]: 5 + 3
Out[1]: 8

In [2]: Out[1] + 5
Out[2]: 13

In [3]: Out
Out[3]: Dict{Int64, Any} with 2 entries:
  2 => 13
  1 => 8
```

!!! note
    由于之前的 REPL 评估的所有输出都保存在 `Out` 变量中，因此如果返回许多大型内存对象（如数组），则需要小心，因为只要对它们的引用仍然保留在 `Out` 中，它们就会被保护，无法被垃圾回收。如果需要删除 `Out` 中对象的引用，可以使用 `empty!(Out)` 清除它存储的整个历史记录，或者使用 `Out[n] = nothing` 清除单个条目。


## TerminalMenus

TerminalMenus 是 Julia REPL 的一个子模块，能够在终端中启用小型、低调的交互式菜单。

### Examples

```julia
import REPL
using REPL.TerminalMenus

options = ["apple", "orange", "grape", "strawberry",
            "blueberry", "peach", "lemon", "lime"]

```

#### RadioMenu

RadioMenu 允许用户从列表中选择一个选项。`request` 函数显示交互式菜单并返回所选选项的索引。如果用户按下 'q' 或 `ctrl-c`，`request` 将返回 `-1`。

```julia
# `pagesize` is the number of items to be displayed at a time.
#  The UI will scroll if the number of options is greater
#   than the `pagesize`
menu = RadioMenu(options, pagesize=4)

# `request` displays the menu and returns the index after the
#   user has selected a choice
choice = request("Choose your favorite fruit:", menu)

if choice != -1
    println("Your favorite fruit is ", options[choice], "!")
else
    println("Menu canceled.")
end

```

请提供您想要翻译的Markdown内容或文本。

```
Choose your favorite fruit:
^  grape
   strawberry
 > blueberry
v  peach
Your favorite fruit is blueberry!
```

#### MultiSelectMenu

MultiSelectMenu 允许用户从列表中选择多个选项。

```julia
# here we use the default `pagesize` 10
menu = MultiSelectMenu(options)

# `request` returns a `Set` of selected indices
# if the menu us canceled (ctrl-c or q), return an empty set
choices = request("Select the fruits you like:", menu)

if length(choices) > 0
    println("You like the following fruits:")
    for i in choices
        println("  - ", options[i])
    end
else
    println("Menu canceled.")
end
```

请提供您希望翻译的Markdown内容或文本。

```
Select the fruits you like:
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
 > [X] orange
   [X] grape
   [ ] strawberry
   [ ] blueberry
   [X] peach
   [ ] lemon
   [ ] lime
You like the following fruits:
  - orange
  - grape
  - peach
```

### Customization / Configuration

#### ConfiguredMenu subtypes

从 Julia 1.6 开始，推荐的配置菜单的方式是通过构造函数。例如，默认的多选菜单

```
julia> menu = MultiSelectMenu(options, pagesize=5);

julia> request(menu) # ASCII is used by default
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   [ ] apple
   [X] orange
   [ ] grape
 > [X] strawberry
v  [ ] blueberry
```

可以用Unicode选择和导航字符来呈现。

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode);

julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   ⬚ apple
   ✓ orange
   ⬚ grape
 → ✓ strawberry
↓  ⬚ blueberry
```

更细粒度的配置也是可能的：

```julia-repl
julia> menu = MultiSelectMenu(options, pagesize=5, charset=:unicode, checked="YEP!", unchecked="NOPE", cursor='⧐');

julia> request(menu)
julia> request(menu)
[press: Enter=toggle, a=all, n=none, d=done, q=abort]
   NOPE apple
   YEP! orange
   NOPE grape
 ⧐ YEP! strawberry
↓  NOPE blueberry
```

除了整体的 `charset` 选项，`RadioMenu` 的可配置选项包括：

  * `cursor::Char='>'|'→'`: 用于光标的字符
  * `up_arrow::Char='^'|'↑'`: 用于上箭头的字符
  * `down_arrow::Char='v'|'↓'`: 用于向下箭头的字符
  * `updown_arrow::Char='I'|'↕'`: 用于单行页面的上下箭头的字符
  * `scroll_wrap::Bool=false`: 可选地在菜单的开始/结束处循环。
  * `ctrl_c_interrupt::Bool=true`: 如果为 `false`，在 ^C 时返回空，如果为 `true` 在 ^C 时抛出 InterruptException()

`MultiSelectMenu` 添加：

  * `checked::String="[X]"|"✓"`：用于已选中的字符串
  * `unchecked::String="[ ]"|"⬚")`: 用于未选中的字符串

您可以创建您自己的新菜单类型。派生自 `TerminalMenus.ConfiguredMenu` 的类型在构造时配置菜单选项。

#### Legacy interface

在 Julia 1.6 之前，并且在整个 Julia 1.x 中仍然支持，可以通过调用 `TerminalMenus.config()` 来配置菜单。

## References

### REPL

```@docs
Base.atreplinit
```

### TerminalMenus

### Menus

```@docs
REPL.TerminalMenus.RadioMenu
REPL.TerminalMenus.MultiSelectMenu
```

#### Configuration

```@docs
REPL.TerminalMenus.Config
REPL.TerminalMenus.MultiSelectConfig
REPL.TerminalMenus.config
```

#### User interaction

```@docs
REPL.TerminalMenus.request
```

#### AbstractMenu extension interface

任何 `AbstractMenu` 的子类型必须是可变的，并且必须包含字段 `pagesize::Int` 和 `pageoffset::Int`。任何子类型还必须实现以下函数：

```@docs
REPL.TerminalMenus.pick
REPL.TerminalMenus.cancel
REPL.TerminalMenus.writeline
```

它还必须实现 `options` 或 `numoptions`：

```@docs
REPL.TerminalMenus.options
REPL.TerminalMenus.numoptions
```

如果子类型没有名为 `selected` 的字段，它也必须实现

```@docs
REPL.TerminalMenus.selected
```

以下内容是可选的，但可以允许额外的自定义：

```@docs
REPL.TerminalMenus.header
REPL.TerminalMenus.keypress
```
