# Running External Programs

Julia 借用了 shell、Perl 和 Ruby 的反引号语法来表示命令。然而，在 Julia 中，编写

```jldoctest
julia> `echo hello`
`echo hello`
```

在多个方面与各种 shell、Perl 或 Ruby 中的行为有所不同：

  * 而不是立即运行命令，反引号创建一个 [`Cmd`](@ref) 对象来表示命令。您可以使用此对象通过管道将命令连接到其他命令，[`run`](@ref) 它，以及 [`read`](@ref) 或 [`write`](@ref) 连接到它。
  * 当命令运行时，Julia 不会捕获其输出，除非你特别安排它。相反，命令的输出默认会发送到 [`stdout`](@ref)，就像使用 `libc` 的 `system` 调用一样。
  * 该命令从不通过 shell 运行。相反，Julia 直接解析命令语法，适当地插入变量并像 shell 一样按单词拆分，遵循 shell 引号语法。该命令作为 `julia` 的直接子进程运行，使用 `fork` 和 `exec` 调用。

!!! note
    以下假设在 Linux 或 MacOS 的 Posix 环境中。在 Windows 上，许多类似的命令，如 `echo` 和 `dir`，并不是外部程序，而是内置于 shell `cmd.exe` 中。运行这些命令的一个选项是调用 `cmd.exe`，例如 `cmd /C echo hello`。或者，Julia 可以在 Cygwin 等 Posix 环境中运行。


这是运行外部程序的简单示例：

```jldoctest
julia> mycommand = `echo hello`
`echo hello`

julia> typeof(mycommand)
Cmd

julia> run(mycommand);
hello
```

`hello` 是 `echo` 命令的输出，发送到 [`stdout`](@ref)。如果外部命令未能成功运行，run 方法将抛出 [`ProcessFailedException`](@ref)。

如果您想读取外部命令的输出，可以使用 [`read`](@ref) 或 [`readchomp`](@ref) 作为替代：

```jldoctest
julia> read(`echo hello`, String)
"hello\n"

julia> readchomp(`echo hello`)
"hello"
```

更一般地，您可以使用 [`open`](@ref) 从外部命令读取或写入。

```jldoctest
julia> open(`less`, "w", stdout) do io
           for i = 1:3
               println(io, i)
           end
       end
1
2
3
```

程序名称和命令中的各个参数可以像访问字符串数组一样被访问和迭代：

```jldoctest
julia> collect(`echo "foo bar"`)
2-element Vector{String}:
 "echo"
 "foo bar"

julia> `echo "foo bar"`[2]
"foo bar"
```

## [Interpolation](@id command-interpolation)

假设你想做一些更复杂的事情，并使用变量 `file` 中的文件名作为命令的参数。你可以像在字符串字面量中一样使用 `$` 进行插值（参见 [Strings](@ref)）：

```jldoctest
julia> file = "/etc/passwd"
"/etc/passwd"

julia> `sort $file`
`sort /etc/passwd`
```

一个在通过 shell 运行外部程序时常见的陷阱是，如果文件名包含对 shell 特殊的字符，它们可能会导致不良行为。例如，假设我们想要对文件 `/Volumes/External HD/data.csv` 的内容进行排序，而不是 `/etc/passwd`。让我们试试看：

```jldoctest
julia> file = "/Volumes/External HD/data.csv"
"/Volumes/External HD/data.csv"

julia> `sort $file`
`sort '/Volumes/External HD/data.csv'`
```

文件名是如何被引用的？Julia 知道 `file` 是作为单个参数进行插值的，因此它会为你引用这个词。实际上，这并不完全准确：`file` 的值从未被 shell 解释，因此实际上不需要引用；引号仅仅是为了向用户展示。即使你将一个值作为 shell 单词的一部分进行插值，这也会有效：

```jldoctest
julia> path = "/Volumes/External HD"
"/Volumes/External HD"

julia> name = "data"
"data"

julia> ext = "csv"
"csv"

julia> `sort $path/$name.$ext`
`sort '/Volumes/External HD/data.csv'`
```

如您所见，`path` 变量中的空格已被适当地转义。但是如果您 *想* 插入多个单词呢？在这种情况下，只需使用数组（或任何其他可迭代容器）：

```jldoctest
julia> files = ["/etc/passwd","/Volumes/External HD/data.csv"]
2-element Vector{String}:
 "/etc/passwd"
 "/Volumes/External HD/data.csv"

julia> `grep foo $files`
`grep foo /etc/passwd '/Volumes/External HD/data.csv'`
```

如果你将一个数组插入到一个 shell 单词中，Julia 会模拟 shell 的 `{a,b,c}` 参数生成：

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> `grep xylophone $names.txt`
`grep xylophone foo.txt bar.txt baz.txt`
```

此外，如果您将多个数组插入到同一个单词中，则模拟了 shell 的笛卡尔积生成行为：

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> exts = ["aux","log"]
2-element Vector{String}:
 "aux"
 "log"

julia> `rm -f $names.$exts`
`rm -f foo.aux foo.log bar.aux bar.log baz.aux baz.log`
```

由于您可以插入字面数组，因此您可以在不需要首先创建临时数组对象的情况下使用此生成功能：

```jldoctest
julia> `rm -rf $["foo","bar","baz","qux"].$["aux","log","pdf"]`
`rm -rf foo.aux foo.log foo.pdf bar.aux bar.log bar.pdf baz.aux baz.log baz.pdf qux.aux qux.log qux.pdf`
```

## Quoting

不可避免地，人们想要编写一些不那么简单的命令，这时就有必要使用引号。以下是在 shell 提示符下的一个简单 Perl 一行代码示例：

```
sh$ perl -le '$|=1; for (0..3) { print }'
0
1
2
3
```

Perl 表达式需要用单引号括起来，原因有两个：一是为了防止空格将表达式分割成多个 shell 单词，二是为了防止像 `$|`（是的，这在 Perl 中是一个变量的名称）这样的 Perl 变量导致插值。在其他情况下，您可能希望使用双引号，以便插值 *确实* 发生：

```
sh$ first="A"
sh$ second="B"
sh$ perl -le '$|=1; print for @ARGV' "1: $first" "2: $second"
1: A
2: B
```

一般来说，Julia 的反引号语法经过精心设计，因此您可以直接将 shell 命令剪切并粘贴到反引号中，它们将正常工作：转义、引用和插值行为与 shell 的相同。唯一的区别是，插值是集成的，并且了解 Julia 对单个字符串值和多个值容器的概念。让我们在 Julia 中尝试上述两个示例：

```jldoctest
julia> A = `perl -le '$|=1; for (0..3) { print }'`
`perl -le '$|=1; for (0..3) { print }'`

julia> run(A);
0
1
2
3

julia> first = "A"; second = "B";

julia> B = `perl -le 'print for @ARGV' "1: $first" "2: $second"`
`perl -le 'print for @ARGV' '1: A' '2: B'`

julia> run(B);
1: A
2: B
```

结果是相同的，Julia 的插值行为模仿了 shell 的行为，并由于 Julia 支持一流的可迭代对象而有所改进，而大多数 shell 使用基于空格分割的字符串，这引入了歧义。在尝试将 shell 命令移植到 Julia 时，首先尝试剪切和粘贴。由于 Julia 在运行命令之前会向您显示命令，您可以轻松且安全地检查其解释，而不会造成任何损害。

## Pipelines

Shell 元字符，例如 `|`、`&` 和 `>`，需要在 Julia 的反引号内进行引用（或转义）：

```jldoctest
julia> run(`echo hello '|' sort`);
hello | sort

julia> run(`echo hello \| sort`);
hello | sort
```

这个表达式调用了 `echo` 命令，并将三个单词作为参数：`hello`、`|` 和 `sort`。结果是打印出一行：`hello | sort`。那么，如何构建一个管道呢？而不是在反引号内使用 `'|'`，而是使用 [`pipeline`](@ref)：

```jldoctest
julia> run(pipeline(`echo hello`, `sort`));
hello
```

这将 `echo` 命令的输出传递给 `sort` 命令。当然，这并不是特别有趣，因为只有一行需要排序，但我们可以做更有趣的事情：

```julia-repl
julia> run(pipeline(`cut -d: -f3 /etc/passwd`, `sort -n`, `tail -n5`))
210
211
212
213
214
```

这会打印出 UNIX 系统上最高的五个用户 ID。`cut`、`sort` 和 `tail` 命令都是作为当前 `julia` 进程的直接子进程被生成的，没有中间的 shell 进程。Julia 自己完成了设置管道和连接文件描述符的工作，这通常是由 shell 完成的。由于 Julia 自己执行这些操作，它能够保持更好的控制，并且可以做一些 shell 无法做到的事情。

Julia 可以并行运行多个命令：

```jldoctest; filter = r"(world\nhello|hello\nworld)"
julia> run(`echo hello` & `echo world`);
world
hello
```

输出的顺序是非确定性的，因为两个 `echo` 进程几乎同时启动，并争先恐后地向它们共享的 [`stdout`](@ref) 描述符进行第一次写入。Julia 允许你将这两个进程的输出通过管道传递给另一个程序：

```jldoctest
julia> run(pipeline(`echo world` & `echo hello`, `sort`));
hello
world
```

在 UNIX 管道的术语中，这里发生的是创建了一个单一的 UNIX 管道对象，并由两个 `echo` 进程写入，而管道的另一端则由 `sort` 命令读取。

IO重定向可以通过将关键字参数`stdin`、`stdout`和`stderr`传递给`pipeline`函数来实现：

```julia
pipeline(`do_work`, stdout=pipeline(`sort`, "out.txt"), stderr="errs.txt")
```

### Avoiding Deadlock in Pipelines

在从单个进程的管道两端进行读写时，重要的是要避免强迫内核缓冲所有数据。

例如，在读取命令的所有输出时，调用 `read(out, String)`，而不是 `wait(process)`，因为前者会主动消耗进程写入的所有数据，而后者则会尝试将数据存储在内核的缓冲区中，同时等待连接的读取器。

另一个常见的解决方案是将管道的读取器和写入器分开到不同的 [`Task`](@ref)：

```julia
writer = @async write(process, "data")
reader = @async do_compute(read(process, String))
wait(writer)
fetch(reader)
```

（通常来说，读者并不是一个单独的任务，因为我们无论如何都会立即 `fetch` 它。）

### Complex Example

高级编程语言、一级命令抽象和进程之间管道的自动设置的结合是强大的。为了让人们感受到可以轻松创建的复杂管道，这里有一些更复杂的示例，抱歉过度使用了 Perl 单行代码：

```jldoctest prefixer; filter = r"([A-B] [0-5])"
julia> prefixer(prefix, sleep) = `perl -nle '$|=1; print "'$prefix' ", $_; sleep '$sleep';'`;

julia> run(pipeline(`perl -le '$|=1; for(0..5){ print; sleep 1 }'`, prefixer("A",2) & prefixer("B",2)));
B 0
A 1
B 2
A 3
B 4
A 5
```

这是一个经典的例子，展示了一个单一生产者为两个并发消费者提供数据：一个 `perl` 进程生成包含数字 0 到 5 的行，而两个并行进程消费该输出，一个在行前加上字母 "A"，另一个加上字母 "B"。哪个消费者获得第一行是非确定性的，但一旦这个竞争获胜，行将由一个进程和另一个进程交替消费。（在 Perl 中设置 `$|=1` 会导致每个打印语句刷新 [`stdout`](@ref) 句柄，这是这个例子正常工作的必要条件。否则，所有输出都会被缓冲，并一次性打印到管道中，只能被一个消费者进程读取。）

这是一个更复杂的多阶段生产者-消费者示例：

```jldoctest prefixer; filter = r"[A-B] [X-Z] [0-5]"
julia> run(pipeline(`perl -le '$|=1; for(0..5){ print; sleep 1 }'`,
           prefixer("X",3) & prefixer("Y",3) & prefixer("Z",3),
           prefixer("A",2) & prefixer("B",2)));
A X 0
B Y 1
A Z 2
B X 3
A Y 4
B Z 5
```

这个例子与前一个类似，不同之处在于有两个阶段的消费者，并且这些阶段具有不同的延迟，因此它们使用不同数量的并行工作者，以保持饱和的吞吐量。

我们强烈建议您尝试所有这些示例，以了解它们是如何工作的。

## `Cmd` Objects

反引号语法创建一个类型为 [`Cmd`](@ref) 的对象。这样的对象也可以直接从现有的 `Cmd` 或参数列表构造：

```julia
run(Cmd(`pwd`, dir=".."))
run(Cmd(["pwd"], detach=true, ignorestatus=true))
```

这允许您通过关键字参数指定 `Cmd` 执行环境的多个方面。例如，`dir` 关键字提供对 `Cmd` 工作目录的控制：

```jldoctest
julia> run(Cmd(`pwd`, dir="/"));
/
```

并且 `env` 关键字允许您设置执行环境变量：

```jldoctest
julia> run(Cmd(`sh -c "echo foo \$HOWLONG"`, env=("HOWLONG" => "ever!",)));
foo ever!
```

查看 [`Cmd`](@ref) 以获取其他关键字参数。 [`setenv`](@ref) 和 [`addenv`](@ref) 命令分别提供了替换或添加 `Cmd` 执行环境变量的另一种方法：

```jldoctest
julia> run(setenv(`sh -c "echo foo \$HOWLONG"`, ("HOWLONG" => "ever!",)));
foo ever!

julia> run(addenv(`sh -c "echo foo \$HOWLONG"`, "HOWLONG" => "ever!"));
foo ever!
```
