```
Core.Intrinsics.atomic_pointermodify(pointer::Ptr{T}, function::(old::T,arg::S)->T, arg::S, order::Symbol) --> old
```

!!! compat "Julia 1.7"
    此函数需要 Julia 1.7 或更高版本。


请参见 [`unsafe_modify!`](@ref Base.unsafe_modify!)。
