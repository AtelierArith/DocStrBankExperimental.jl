```
joinpath(parts::AbstractString...) -> String
joinpath(parts::Vector{AbstractString}) -> String
joinpath(parts::Tuple{AbstractString}) -> String
```

将路径组件连接成完整路径。如果某个参数是绝对路径或（在 Windows 上）具有与前面路径的连接计算出的驱动器不匹配的驱动器规范，则丢弃先前的组件。

关于 Windows 的说明，由于每个驱动器都有当前目录，`joinpath("c:", "foo")` 表示相对于驱动器 "c:" 的当前目录的路径，因此这等于 "c:foo"，而不是 "c:\foo"。此外，`joinpath` 将其视为非绝对路径，并忽略驱动器字母的大小写，因此 `joinpath("C:\A","c:b") = "C:\A\b"`。

# 示例

```jldoctest
julia> joinpath("/home/myuser", "example.jl")
"/home/myuser/example.jl"
```

```jldoctest
julia> joinpath(["/home/myuser", "example.jl"])
"/home/myuser/example.jl"
```
