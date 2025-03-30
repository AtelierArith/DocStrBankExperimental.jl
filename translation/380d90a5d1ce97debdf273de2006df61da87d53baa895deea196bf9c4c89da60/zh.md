```
@generated f
```

`@generated` 用于注解将要生成的函数。在生成的函数体内，只能读取参数的类型（而不是值）。该函数返回一个在调用函数时评估的引用表达式。`@generated` 宏不应在改变全局作用域或依赖可变元素的函数上使用。

有关更多详细信息，请参见 [Metaprogramming](@ref)。

# 示例

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```
