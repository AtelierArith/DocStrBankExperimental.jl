```
getproperty(value, name::Symbol)
getproperty(value, name::Symbol, order::Symbol)
```

语法 `a.b` 调用 `getproperty(a, :b)`。语法 `@atomic order a.b` 调用 `getproperty(a, :b, :order)`，而语法 `@atomic a.b` 调用 `getproperty(a, :b, :sequentially_consistent)`。

# 示例

```jldoctest
julia> struct MyType{T <: Number}
           x::T
       end

julia> function Base.getproperty(obj::MyType, sym::Symbol)
           if sym === :special
               return obj.x + 1
           else # fallback to getfield
               return getfield(obj, sym)
           end
       end

julia> obj = MyType(1);

julia> obj.special
2

julia> obj.x
1
```

只有在必要时才应重载 `getproperty`，因为如果语法 `obj.f` 的行为不寻常，可能会造成困惑。还要注意，使用方法通常更可取。有关更多信息，请参见此风格指南文档：[Prefer exported methods over direct field access](@ref)。

另请参见 [`getfield`](@ref Core.getfield)，[`propertynames`](@ref Base.propertynames) 和 [`setproperty!`](@ref Base.setproperty!)。
