```
宏
```

`宏` 定义了一种将生成的代码插入程序的方法。宏将一系列参数表达式映射到返回的表达式，结果表达式直接替换到调用宏的程序中的位置。宏是一种运行生成代码而不调用 [`eval`](@ref Main.eval) 的方式，因为生成的代码简单地成为周围程序的一部分。宏参数可以包括表达式、字面值和符号。可以为可变数量的参数（varargs）定义宏，但不接受关键字参数。每个宏还隐式地接收参数 `__source__`，它包含宏被调用的行号和文件名，以及 `__module__`，它是宏展开的模块。

有关如何编写宏的更多信息，请参见手册中的 [元编程](@ref) 部分。

# 示例

```jldoctest
julia> macro sayhello(name)
           return :( println("Hello, ", $name, "!") )
       end
@sayhello (宏有 1 个方法)

julia> @sayhello "Charlie"
Hello, Charlie!

julia> macro saylots(x...)
           return :( println("Say: ", $(x...)) )
       end
@saylots (宏有 1 个方法)

julia> @saylots "hey " "there " "friend"
Say: hey there friend
```
