# Networking and Streams

Julia 提供了丰富的接口来处理流式 I/O 对象，如终端、管道和 TCP 套接字。这些对象允许以流式方式发送和接收数据，这意味着数据会在可用时按顺序处理。尽管在系统级别上该接口是异步的，但对程序员来说是以同步的方式呈现的。这是通过大量使用 Julia 协作线程 ([coroutine](@ref man-tasks)) 功能实现的。

## Basic Stream I/O

所有 Julia 流都至少暴露一个 [`read`](@ref) 和一个 [`write`](@ref) 方法，将流作为它们的第一个参数，例如：

```julia-repl
julia> write(stdout, "Hello World");  # suppress return value 11 with ;
Hello World
julia> read(stdin, Char)

'\n': ASCII/Unicode U+000a (category Cc: Other, control)
```

注意到 [`write`](@ref) 返回 11，即写入 [`stdout`](@ref) 的字节数（在 `"Hello World"` 中），但这个返回值被 `;` 抑制了。

这里再次按下了 Enter，以便 Julia 能够读取换行符。现在，正如您从这个例子中看到的，[`write`](@ref) 将要写入的数据作为第二个参数，而 [`read`](@ref) 将要读取的数据类型作为第二个参数。

例如，要读取一个简单的字节数组，我们可以这样做：

```julia-repl
julia> x = zeros(UInt8, 4)
4-element Array{UInt8,1}:
 0x00
 0x00
 0x00
 0x00

julia> read!(stdin, x)
abcd
4-element Array{UInt8,1}:
 0x61
 0x62
 0x63
 0x64
```

然而，由于这有些繁琐，因此提供了几种便利的方法。例如，我们可以将上述内容写成：

```julia-repl
julia> read(stdin, 4)
abcd
4-element Array{UInt8,1}:
 0x61
 0x62
 0x63
 0x64
```

或者如果我们想要读取整行的话：

```julia-repl
julia> readline(stdin)
abcd
"abcd"
```

请注意，根据您的终端设置，您的 TTY（“电传打字机终端”）可能是行缓冲的，因此在将 `stdin` 数据发送到 Julia 之前可能需要额外的回车。当在 TTY 中从命令行运行 Julia 时，输出默认发送到控制台，标准输入则从键盘读取。

要从 [`stdin`](@ref) 读取每一行，可以使用 [`eachline`](@ref)：

```julia
for line in eachline(stdin)
    print("Found $line")
end
```

或 [`read`](@ref) 如果你想按字符读取：

```julia
while !eof(stdin)
    x = read(stdin, Char)
    println("Found: $x")
end
```

## Text I/O

请注意，上述提到的 [`write`](@ref) 方法在二进制流上操作。特别是，值不会转换为任何规范的文本表示，而是按原样写出：

```jldoctest
julia> write(stdout, 0x61);  # suppress return value 1 with ;
a
```

注意到 `a` 是通过 [`stdout`](@ref) 函数写入 [`write`](@ref) 的，并且返回的值是 `1`（因为 `0x61` 是一个字节）。

对于文本输入/输出，根据您的需求使用 [`print`](@ref) 或 [`show`](@ref) 方法（有关这两种方法之间差异的详细讨论，请参见文档）：

```jldoctest
julia> print(stdout, 0x61)
97
```

请参阅 [Custom pretty-printing](@ref man-custom-pretty-printing) 以获取有关如何为自定义类型实现显示方法的更多信息。

## IO Output Contextual Properties

有时，IO 输出可以受益于将上下文信息传递到显示方法的能力。[`IOContext`](@ref) 对象提供了将任意元数据与 IO 对象关联的框架。例如，`:compact => true` 向 IO 对象添加了一个提示参数，指示调用的显示方法应该打印更短的输出（如果适用）。有关常见属性的列表，请参见 `4d61726b646f776e2e436f64652822222c2022494f436f6e746578742229_40726566` 文档。

## Working with Files

您可以使用 `write(filename::String, content)` 方法将内容写入文件：

```julia-repl
julia> write("hello.txt", "Hello, World!")
13
```

*(`13` 是写入的字节数。)*

您可以使用 `read(filename::String)` 方法读取文件的内容，或者使用 `read(filename::String, String)` 将内容作为字符串读取：

```julia-repl
julia> read("hello.txt", String)
"Hello, World!"
```

### Advanced: streaming files

`read` 和 `write` 方法允许您读取和写入文件内容。像许多其他环境一样，Julia 也有一个 [`open`](@ref) 函数，它接受一个文件名并返回一个 [`IOStream`](@ref) 对象，您可以使用它从文件中读取和写入内容。例如，如果我们有一个文件 `hello.txt`，其内容为 `Hello, World!`：

```julia-repl
julia> f = open("hello.txt")
IOStream(<file hello.txt>)

julia> readlines(f)
1-element Array{String,1}:
 "Hello, World!"
```

如果您想写入文件，可以使用写入（`"w"`）标志打开它：

```julia-repl
julia> f = open("hello.txt","w")
IOStream(<file hello.txt>)

julia> write(f,"Hello again.")
12
```

如果此时检查 `hello.txt` 的内容，您会注意到它是空的；实际上还没有任何内容写入磁盘。这是因为 `IOStream` 必须在写入实际刷新到磁盘之前关闭：

```julia-repl
julia> close(f)
```

再次检查 `hello.txt` 将显示其内容已被更改。

打开文件、对其内容进行操作，然后再关闭它是一个非常常见的模式。为了简化这个过程，存在另一个调用 [`open`](@ref)，它将一个函数作为第一个参数，将文件名作为第二个参数，打开文件，使用文件作为参数调用该函数，然后再关闭它。例如，给定一个函数：

```julia
function read_and_capitalize(f::IOStream)
    return uppercase(read(f, String))
end
```

你可以拨打：

```julia-repl
julia> open(read_and_capitalize, "hello.txt")
"HELLO AGAIN."
```

要打开 `hello.txt`，调用 `read_and_capitalize`，关闭 `hello.txt` 并返回大写的内容。

为了避免甚至需要定义一个命名函数，您可以使用 `do` 语法，它会动态创建一个匿名函数：

```julia-repl
julia> open("hello.txt") do f
           uppercase(read(f, String))
       end
"HELLO AGAIN."
```

如果您想将标准输出重定向到文件

```# Open file for writing
out_file = open("output.txt", "w")

# Redirect stdout to file
redirect_stdout(out_file) do
    # Your code here
    println("This output goes to `out_file` via the `stdout` variable.")
end

# Close file
close(out_file)

```

将标准输出重定向到文件可以帮助您保存和分析程序输出，自动化流程，并满足合规要求。

## A simple TCP example

让我们直接开始一个涉及 TCP 套接字的简单示例。此功能位于一个名为 `Sockets` 的标准库包中。我们首先创建一个简单的服务器：

```julia-repl
julia> using Sockets

julia> errormonitor(@async begin
           server = listen(2000)
           while true
               sock = accept(server)
               println("Hello World\n")
           end
       end)
Task (runnable) @0x00007fd31dc11ae0
```

对于熟悉 Unix 套接字 API 的人来说，这些方法名称会感到熟悉，尽管它们的用法比原始 Unix 套接字 API 简单一些。第一次调用 [`listen`](@ref) 将创建一个服务器，等待在指定端口（在此情况下为 2000）上接收传入连接。相同的函数也可以用于创建各种其他类型的服务器：

```julia-repl
julia> listen(2000) # Listens on localhost:2000 (IPv4)
Sockets.TCPServer(active)

julia> listen(ip"127.0.0.1",2000) # Equivalent to the first
Sockets.TCPServer(active)

julia> listen(ip"::1",2000) # Listens on localhost:2000 (IPv6)
Sockets.TCPServer(active)

julia> listen(IPv4(0),2001) # Listens on port 2001 on all IPv4 interfaces
Sockets.TCPServer(active)

julia> listen(IPv6(0),2001) # Listens on port 2001 on all IPv6 interfaces
Sockets.TCPServer(active)

julia> listen("testsocket") # Listens on a UNIX domain socket
Sockets.PipeServer(active)

julia> listen("\\\\.\\pipe\\testsocket") # Listens on a Windows named pipe
Sockets.PipeServer(active)
```

请注意，最后一次调用的返回类型是不同的。这是因为该服务器不监听 TCP，而是监听命名管道（Windows）或 UNIX 域套接字。还要注意，Windows 命名管道格式必须遵循特定模式，以便名称前缀（`\\.\pipe\`）唯一标识 [file type](https://docs.microsoft.com/windows/desktop/ipc/pipe-names)。TCP 和命名管道或 UNIX 域套接字之间的区别是微妙的，涉及到 [`accept`](@ref) 和 [`connect`](@ref) 方法。`4d61726b646f776e2e436f64652822222c20226163636570742229_40726566` 方法检索与我们刚刚创建的服务器连接的客户端，而 `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` 函数使用指定的方法连接到服务器。`4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566` 函数接受与 [`listen`](@ref) 相同的参数，因此，假设环境（即主机、当前工作目录等）相同，您应该能够将与监听建立连接时相同的参数传递给 `4d61726b646f776e2e436f64652822222c2022636f6e6e6563742229_40726566`。所以让我们试一下（在创建了上面的服务器之后）：

```julia-repl
julia> connect(2000)
TCPSocket(open, 0 bytes waiting)

julia> Hello World
```

正如预期的那样，我们看到了“Hello World”的输出。那么，让我们实际分析一下幕后发生了什么。当我们调用 [`connect`](@ref) 时，我们连接到了刚刚创建的服务器。与此同时，accept 函数返回一个服务器端连接到新创建的套接字，并打印“Hello World”以指示连接成功。

Julia 的一个巨大优势在于，尽管 I/O 实际上是异步发生的，但 API 是同步暴露的，因此我们不必担心回调，甚至不必确保服务器能够运行。当我们调用 [`connect`](@ref) 时，当前任务会等待连接建立，只有在完成后才继续执行。在这个暂停期间，服务器任务恢复执行（因为现在有了连接请求），接受连接，打印消息并等待下一个客户端。读取和写入的工作方式是相同的。要看到这一点，可以考虑以下简单的回声服务器：

```julia-repl
julia> errormonitor(@async begin
           server = listen(2001)
           while true
               sock = accept(server)
               @async while isopen(sock)
                   write(sock, readline(sock, keep=true))
               end
           end
       end)
Task (runnable) @0x00007fd31dc12e60

julia> clientside = connect(2001)
TCPSocket(RawFD(28) open, 0 bytes waiting)

julia> errormonitor(@async while isopen(clientside)
           write(stdout, readline(clientside, keep=true))
       end)
Task (runnable) @0x00007fd31dc11870

julia> println(clientside,"Hello World from the Echo Server")
Hello World from the Echo Server
```

与其他流一样，使用 [`close`](@ref) 来断开套接字：

```julia-repl
julia> close(clientside)
```

## Resolving IP Addresses

其中一个不遵循 [`connect`](@ref) 方法的 [`listen`](@ref) 方法是 `connect(host::String,port)`，它将尝试在由 `host` 参数给定的主机上连接由 `port` 参数给定的端口。它允许你做一些事情，比如：

```julia-repl
julia> connect("google.com", 80)
TCPSocket(RawFD(30) open, 0 bytes waiting)
```

在此功能的基础上是 [`getaddrinfo`](@ref)，它将执行适当的地址解析：

```julia-repl
julia> getaddrinfo("google.com")
ip"74.125.226.225"
```

## Asynchronous I/O

所有由 [`Base.read`](@ref) 和 [`Base.write`](@ref) 暴露的所有 I/O 操作都可以通过使用 [coroutines](@ref man-tasks) 异步执行。您可以使用 [`@async`](@ref) 宏创建一个新的协程来从流中读取或写入：

```julia-repl
julia> task = @async open("foo.txt", "w") do io
           write(io, "Hello, World!")
       end;

julia> wait(task)

julia> readlines("foo.txt")
1-element Array{String,1}:
 "Hello, World!"
```

在遇到需要同时执行多个异步操作并等待它们全部完成的情况时，这很常见。您可以使用 [`@sync`](@ref) 宏来使您的程序阻塞，直到它所包装的所有协程都已退出：

```julia-repl
julia> using Sockets

julia> @sync for hostname in ("google.com", "github.com", "julialang.org")
           @async begin
               conn = connect(hostname, 80)
               write(conn, "GET / HTTP/1.1\r\nHost:$(hostname)\r\n\r\n")
               readline(conn, keep=true)
               println("Finished connection to $(hostname)")
           end
       end
Finished connection to google.com
Finished connection to julialang.org
Finished connection to github.com
```

## Multicast

Julia 支持 [multicast](https://datatracker.ietf.org/doc/html/rfc1112) 通过 IPv4 和 IPv6 使用用户数据报协议 ([UDP](https://datatracker.ietf.org/doc/html/rfc768) ) 作为传输。

与传输控制协议 ([TCP](https://datatracker.ietf.org/doc/html/rfc793)) 不同，UDP 几乎不对应用程序的需求做出任何假设。TCP 提供流量控制（它加速和减速以最大化吞吐量）、可靠性（丢失或损坏的数据包会自动重传）、排序（数据包在交给应用程序之前由操作系统排序）、段大小以及会话的建立和拆除。UDP 不提供此类功能。

UDP的一个常见用途是在多播应用中。TCP是一种有状态的协议，用于两个设备之间的通信。UDP可以使用特殊的多播地址，允许多个设备之间的同时通信。

### Receiving IP Multicast Packets

要通过UDP多播传输数据，只需在套接字上`recv`，将返回接收到的第一个数据包。请注意，这可能不是您发送的第一个数据包！

```julia
using Sockets
group = ip"228.5.6.7"
socket = Sockets.UDPSocket()
bind(socket, ip"0.0.0.0", 6789)
join_multicast_group(socket, group)
println(String(recv(socket)))
leave_multicast_group(socket, group)
close(socket)
```

### Sending IP Multicast Packets

要通过UDP多播传输数据，只需`send`到套接字。请注意，发送者不必加入多播组。

```julia
using Sockets
group = ip"228.5.6.7"
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv4")
close(socket)
```

### IPv6 Example

这个示例提供了与之前程序相同的功能，但使用IPv6作为网络层协议。

听众：

```julia
using Sockets
group = Sockets.IPv6("ff05::5:6:7")
socket = Sockets.UDPSocket()
bind(socket, Sockets.IPv6("::"), 6789)
join_multicast_group(socket, group)
println(String(recv(socket)))
leave_multicast_group(socket, group)
close(socket)
```

发件人：

```julia
using Sockets
group = Sockets.IPv6("ff05::5:6:7")
socket = Sockets.UDPSocket()
send(socket, group, 6789, "Hello over IPv6")
close(socket)
```
