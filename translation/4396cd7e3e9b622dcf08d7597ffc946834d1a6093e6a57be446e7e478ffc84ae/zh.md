```
Base.@nospecializeinfer function f(args...)
    @nospecialize ...
    ...
end
Base.@nospecializeinfer f(@nospecialize args...) = ...
```

告诉编译器使用 `@nospecialize` 参数的声明类型来推断 `f`。这可以用来限制推断期间编译器生成的特化数量。

# 示例

```julia
julia> f(A::AbstractArray) = g(A)
f (generic function with 1 method)

julia> @noinline Base.@nospecializeinfer g(@nospecialize(A::AbstractArray)) = A[1]
g (generic function with 1 method)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Any
└──      return %1
) => Any
```

在这个例子中，`f` 将针对 `A` 的每个特定类型进行推断，但 `g` 只会使用声明的参数类型 `A::AbstractArray` 进行一次推断，这意味着编译器不太可能在其上看到过多的推断时间，因为它无法推断其具体的返回类型。如果没有 `@nospecializeinfer`，`f([1.0])` 将推断 `g` 的返回类型为 `Float64`，这表明尽管禁止了特化代码生成，推断仍然针对 `g(::Vector{Float64})` 进行了。

!!! compat "Julia 1.10"
    使用 `Base.@nospecializeinfer` 需要 Julia 版本 1.10。

