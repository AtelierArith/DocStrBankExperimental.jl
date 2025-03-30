```
@Kwargs{key1::Type1, key2::Type2, ...}
```

这个宏提供了一种方便的方式来构造关键字参数的类型表示，语法与 [`@NamedTuple`](@ref) 相同。例如，当我们有一个函数调用像 `func([positional arguments]; kw1=1.0, kw2="2")` 时，我们可以使用这个宏将关键字参数的内部类型表示构造为 `@Kwargs{kw1::Float64, kw2::String}`。该宏的语法专门设计用于简化关键字方法的签名类型，以便在堆栈跟踪视图中打印时更清晰。

```julia
julia> @Kwargs{init::Int} # 关键字参数的内部表示
Base.Pairs{Symbol, Int64, Tuple{Symbol}, @NamedTuple{init::Int64}}

julia> sum("julia"; init=1)
ERROR: MethodError: no method matching +(::Char, ::Char)
函数 `+` 存在，但没有为这种参数类型组合定义方法。

最接近的候选者是：
  +(::Any, ::Any, ::Any, ::Any...)
   @ Base operators.jl:585
  +(::Integer, ::AbstractChar)
   @ Base char.jl:247
  +(::T, ::Integer) where T<:AbstractChar
   @ Base char.jl:237

堆栈跟踪：
  [1] add_sum(x::Char, y::Char)
    @ Base ./reduce.jl:24
  [2] BottomRF
    @ Base ./reduce.jl:86 [内联]
  [3] _foldl_impl(op::Base.BottomRF{typeof(Base.add_sum)}, init::Int64, itr::String)
    @ Base ./reduce.jl:62
  [4] foldl_impl(op::Base.BottomRF{typeof(Base.add_sum)}, nt::Int64, itr::String)
    @ Base ./reduce.jl:48 [内联]
  [5] mapfoldl_impl(f::typeof(identity), op::typeof(Base.add_sum), nt::Int64, itr::String)
    @ Base ./reduce.jl:44 [内联]
  [6] mapfoldl(f::typeof(identity), op::typeof(Base.add_sum), itr::String; init::Int64)
    @ Base ./reduce.jl:175 [内联]
  [7] mapreduce(f::typeof(identity), op::typeof(Base.add_sum), itr::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:307 [内联]
  [8] sum(f::typeof(identity), a::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:535 [内联]
  [9] sum(a::String; kw::@Kwargs{init::Int64})
    @ Base ./reduce.jl:564 [内联]
 [10] 顶级作用域
    @ REPL[12]:1
```

!!! compat "Julia 1.10"
    这个宏自 Julia 1.10 起可用。

