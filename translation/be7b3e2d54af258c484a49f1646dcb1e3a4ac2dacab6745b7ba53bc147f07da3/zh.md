```
isassigned(ref::RefValue) -> Bool
```

测试给定的 [`Ref`](@ref) 是否与一个值相关联。对于位类型对象的 [`Ref`](@ref)，这总是为真。如果引用未定义，则返回 `false`。

# 示例

```jldoctest
julia> ref = Ref{Function}()
Base.RefValue{Function}(#undef)

julia> isassigned(ref)
false

julia> ref[] = (foobar(x) = x)
foobar (generic function with 1 method)

julia> isassigned(ref)
true

julia> isassigned(Ref{Int}())
true
```
