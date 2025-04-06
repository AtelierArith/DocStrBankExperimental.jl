```
“展开”运算符 `...` 表示一系列参数。`...` 可以在函数定义中使用，以指示该函数接受任意数量的参数。`...` 还可以用于将函数应用于一系列参数。

# 示例

```

jldoctest julia> add(xs...) = reduce(+, xs) add (generic function with 1 method)

julia> add(1, 2, 3, 4, 5) 15

julia> add([1, 2, 3]...) 6

julia> add(7, 1:100..., 1000:1100...) 111107

```

```
