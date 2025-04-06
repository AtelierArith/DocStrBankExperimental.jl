# printf() and stdio in the Julia runtime

## [Libuv wrappers for stdio](@id Libuv-wrappers-for-stdio)

`julia.h` 定义了 [libuv](https://docs.libuv.org) 的包装器，用于 `stdio.h` 流：

```c
uv_stream_t *JL_STDIN;
uv_stream_t *JL_STDOUT;
uv_stream_t *JL_STDERR;
```

... 和相应的输出函数：

```c
int jl_printf(uv_stream_t *s, const char *format, ...);
int jl_vprintf(uv_stream_t *s, const char *format, va_list args);
```

这些 `printf` 函数在 `src/` 和 `cli/` 目录中的 `.c` 文件中使用，任何需要标准输入输出的地方都确保以统一的方式处理输出缓冲。

In special cases, like signal handlers, where the full libuv infrastructure is too heavy, `jl_safe_printf()` can be used to [`write(2)`](@ref) directly to `STDERR_FILENO`:

```c
void jl_safe_printf(const char *str, ...);
```

## Interface between JL_STD* and Julia code

[`Base.stdin`](@ref)、[`Base.stdout`](@ref) 和 [`Base.stderr`](@ref) 被绑定到运行时中定义的 `JL_STD*` libuv 流。

Julia的`__init__()`函数（在`base/sysimg.jl`中）调用`reinit_stdio()`（在`base/stream.jl`中）来为[`Base.stdin`](@ref)、[`Base.stdout`](@ref)和[`Base.stderr`](@ref)创建Julia对象。

`reinit_stdio()` 使用 [`ccall`](@ref) 来检索指向 `JL_STD*` 的指针，并调用 `jl_uv_handle_type()` 来检查每个流的类型。然后，它创建一个 Julia `Base.IOStream`、`Base.TTY` 或 `Base.PipeEndpoint` 对象来表示每个流，例如：

```
$ julia -e 'println(typeof((stdin, stdout, stderr)))'
Tuple{Base.TTY,Base.TTY,Base.TTY}

$ julia -e 'println(typeof((stdin, stdout, stderr)))' < /dev/null 2>/dev/null
Tuple{IOStream,Base.TTY,IOStream}

$ echo hello | julia -e 'println(typeof((stdin, stdout, stderr)))' | cat
Tuple{Base.PipeEndpoint,Base.PipeEndpoint,Base.TTY}
```

[`Base.read`](@ref) 和 [`Base.write`](@ref) 方法用于这些流，使用 [`ccall`](@ref) 来调用 `src/jl_uv.c` 中的 libuv 包装器，例如：

```
stream.jl: function write(s::IO, p::Ptr, nb::Integer)
               -> ccall(:jl_uv_write, ...)
  jl_uv.c:          -> int jl_uv_write(uv_stream_t *stream, ...)
                        -> uv_write(uvw, stream, buf, ...)
```

## printf() during initialization

`jl_printf()` 等依赖的 libuv 流在运行时初始化的中间阶段之前不可用（请参见 `init.c`，`init_stdio()`）。 在此之前需要打印的错误消息或警告通过以下机制路由到标准 C 库的 `fwrite()` 函数：

在 `sys.c` 中，`JL_STD*` 流指针被静态初始化为整数常量：`STD*_FILENO (0, 1 和 2)`。在 `jl_uv.c` 中，`jl_uv_puts()` 函数检查其 `uv_stream_t* stream` 参数，并在流设置为 `STDOUT_FILENO` 或 `STDERR_FILENO` 时调用 `fwrite()`。

这允许在运行时统一使用 `jl_printf()`，无论在初始化完成之前是否可以到达任何特定的代码。

## [Legacy `ios.c` library](@id Legacy-ios.c-library)

`src/support/ios.c` 库继承自 [femtolisp](https://github.com/JeffBezanson/femtolisp)。它提供跨平台的缓冲文件 IO 和内存临时缓冲区。

`ios.c` 仍然被以下内容使用：

  * `src/flisp/*.c`
  * `src/dump.c` – 用于序列化文件 IO 和内存缓冲区。
  * `src/staticdata.c` – 用于序列化文件输入输出和内存缓冲区。
  * `base/iostream.jl` – 用于文件输入输出（参见 `base/fs.jl` 的 libuv 等效项）。

在这些模块中，`ios.c` 的使用主要是自包含的，并与 libuv I/O 系统分开。然而，有 [one place](https://github.com/JuliaLang/julia/blob/master/src/flisp/print.c#L654)，在这里，femtolisp 通过一个遗留的 `ios_t` 流调用 `jl_printf()`。

在 `ios.h` 中有一个黑客技巧，使得 `ios_t.bm` 字段与 `uv_stream_t.type` 对齐，并确保用于 `ios_t.bm` 的值不会与有效的 `UV_HANDLE_TYPE` 值重叠。这允许 `uv_stream_t` 指针指向 `ios_t` 流。

这是必要的，因为 `jl_printf()` 的调用者 `jl_static_show()` 是通过 femtolisp 的 `fl_print()` 函数传递一个 `ios_t` 流。Julia 的 `jl_uv_puts()` 函数对此有特殊处理：

```c
if (stream->type > UV_HANDLE_TYPE_MAX) {
    return ios_write((ios_t*)stream, str, n);
}
```
