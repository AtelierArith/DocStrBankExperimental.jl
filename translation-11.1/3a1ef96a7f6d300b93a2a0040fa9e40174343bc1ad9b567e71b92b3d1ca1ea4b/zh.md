# I/O and Network

## General I/O

```@docs
Base.stdout
Base.stderr
Base.stdin
Base.read(::AbstractString)
Base.write(::AbstractString, ::Any)
Base.open
Base.IOStream
Base.IOBuffer
Base.take!(::Base.GenericIOBuffer)
Base.Pipe
Base.link_pipe!
Base.fdio
Base.flush
Base.close
Base.closewrite
Base.write
Base.read
Base.read!
Base.readbytes!
Base.unsafe_read
Base.unsafe_write
Base.readeach
Base.peek
Base.position
Base.seek
Base.seekstart
Base.seekend
Base.skip
Base.mark
Base.unmark
Base.reset(::IO)
Base.ismarked
Base.eof
Base.isreadonly
Base.iswritable
Base.isreadable
Base.isexecutable
Base.isopen
Base.fd
Base.redirect_stdio
Base.redirect_stdout
Base.redirect_stdout(::Function, ::Any)
Base.redirect_stderr
Base.redirect_stderr(::Function, ::Any)
Base.redirect_stdin
Base.redirect_stdin(::Function, ::Any)
Base.readchomp
Base.truncate
Base.skipchars
Base.countlines
Base.PipeBuffer
Base.readavailable
Base.IOContext
Base.IOContext(::IO, ::Pair)
Base.IOContext(::IO, ::IOContext)
```

## Text I/O

```@docs
Base.show(::IO, ::Any)
Base.summary
Base.print
Base.println
Base.printstyled
Base.sprint
Base.showerror
Base.dump
Meta.@dump
Base.readline
Base.readuntil
Base.readlines
Base.eachline
Base.copyline
Base.copyuntil
Base.displaysize
```

## [Multimedia I/O](@id Multimedia-I/O)

正如文本输出通过 [`print`](@ref) 执行，用户定义的类型可以通过重载 [`show`](@ref) 来指示其文本表示，Julia 提供了一种标准化的机制用于丰富的多媒体输出（如图像、格式化文本，甚至音频和视频），由三个部分组成：

  * 一个函数 [`display(x)`](@ref) 用于请求一个 Julia 对象 `x` 的最丰富可用多媒体显示（带有纯文本后备）。
  * 重载 [`show`](@ref) 允许用户指示用户定义类型的任意多媒体表示（通过标准 MIME 类型键入）。
  * 多媒体支持的显示后端可以通过子类化通用 [`AbstractDisplay`](@ref) 类型进行注册，并通过 [`pushdisplay`](@ref) 将它们推送到显示后端的堆栈中。

基础的 Julia 运行时仅提供纯文本显示，但可以通过加载外部模块或使用图形化的 Julia 环境（例如基于 IPython 的 IJulia 笔记本）来启用更丰富的显示。

```@docs
Base.AbstractDisplay
Base.Multimedia.display
Base.Multimedia.redisplay
Base.Multimedia.displayable
Base.show(::IO, ::Any, ::Any)
Base.Multimedia.showable
Base.repr(::MIME, ::Any)
Base.MIME
Base.@MIME_str
```

如上所述，还可以定义新的显示后端。例如，一个可以在窗口中显示 PNG 图像的模块可以将此功能注册到 Julia，这样在具有 PNG 表示的类型上调用 [`display(x)`](@ref) 时，将自动使用模块的窗口显示图像。

为了定义一个新的显示后端，首先应该创建一个抽象类 [`AbstractDisplay`](@ref) 的子类型 `D`。然后，对于每个可以在 `D` 上显示的 MIME 类型（`mime` 字符串），应该定义一个函数 `display(d::D, ::MIME"mime", x) = ...`，该函数将 `x` 作为该 MIME 类型显示，通常通过调用 [`show(io, mime, x)`](@ref) 或 [`repr(io, mime, x)`](@ref)。如果 `x` 不能作为该 MIME 类型显示，则应抛出 [`MethodError`](@ref)；如果调用 `show` 或 `repr`，这将是自动的。最后，应该定义一个函数 `display(d::D, x)`，该函数查询 [`showable(mime, x)`](@ref) 以获取 `D` 支持的 `mime` 类型，并显示“最佳”类型；如果未找到 `x` 的支持 MIME 类型，则应抛出 `MethodError`。类似地，一些子类型可能希望重写 [`redisplay(d::D, ...)`](@ref Base.Multimedia.redisplay)。（同样，应该 `import Base.display` 以向 `display` 添加新方法。）这些函数的返回值取决于实现（因为在某些情况下，返回某种类型的显示“句柄”可能是有用的）。然后，可以直接调用 `D` 的显示函数，但也可以通过将新的显示推送到显示后端堆栈中，自动从 [`display(x)`](@ref) 调用它们：

```@docs
Base.Multimedia.pushdisplay
Base.Multimedia.popdisplay
Base.Multimedia.TextDisplay
Base.Multimedia.istextmime
```

## Network I/O

```@docs
Base.bytesavailable
Base.ntoh
Base.hton
Base.ltoh
Base.htol
Base.ENDIAN_BOM
```
