```
Pipe()
```

构造一个未初始化的 Pipe 对象，特别用于多个进程之间的 IO 通信。

如果在进程生成中使用该对象，管道的适当端将自动初始化。这对于在进程管道中轻松获取引用非常有用，例如：

```
julia> err = Pipe()

# 在此之后，`err` 将被初始化，您可以从 `err` 管道读取 `foo` 的
# stderr，或者将 `err` 传递给其他管道。
julia> run(pipeline(pipeline(`foo`, stderr=err), `cat`), wait=false)

# 现在销毁管道的写入部分，以便读取部分将获得 EOF
julia> closewrite(err)

julia> read(err, String)
"stderr messages"
```

另请参见 [`Base.link_pipe!`](@ref).
