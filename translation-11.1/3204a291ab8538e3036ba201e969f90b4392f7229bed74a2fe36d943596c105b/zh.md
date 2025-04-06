```
@__DIR__ -> String
```

宏用于获取当前目录的绝对路径作为字符串。

如果在脚本中，返回包含 `@__DIR__` 宏调用的脚本的目录。如果从 REPL 运行或通过 `julia -e <expr>` 进行评估，则返回当前工作目录。

# 示例

该示例通过在与当前工作目录不同的目录中创建一个简单脚本，并执行两个命令，说明了 `@__DIR__` 和 `pwd()` 的行为差异：

```julia-repl
julia> cd("/home/JuliaUser") # 工作目录

julia> # 在 /home/JuliaUser/Projects 创建脚本
       open("/home/JuliaUser/Projects/test.jl","w") do io
           print(io, """
               println("@__DIR__ = ", @__DIR__)
               println("pwd() = ", pwd())
           """)
       end

julia> # 输出脚本目录和当前工作目录
       include("/home/JuliaUser/Projects/test.jl")
@__DIR__ = /home/JuliaUser/Projects
pwd() = /home/JuliaUser
```
