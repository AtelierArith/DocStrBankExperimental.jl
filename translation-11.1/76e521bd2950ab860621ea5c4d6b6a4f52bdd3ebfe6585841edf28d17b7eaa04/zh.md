```
Set{T} <: AbstractSet{T}
```

`Set` 是可变容器，提供快速的成员测试。

`Set` 对集合操作如 `in`、`union` 和 `intersect` 有高效的实现。`Set` 中的元素是唯一的，这由元素的 `isequal` 定义决定。`Set` 中元素的顺序是实现细节，不能依赖。

另请参见: [`AbstractSet`](@ref), [`BitSet`](@ref), [`Dict`](@ref), [`push!`](@ref), [`empty!`](@ref), [`union!`](@ref), [`in`](@ref), [`isequal`](@ref)

# 示例

```jldoctest; filter = r"^  '.'"ma
julia> s = Set("aaBca")
Set{Char} with 3 elements:
  'a'
  'c'
  'B'

julia> push!(s, 'b')
Set{Char} with 4 elements:
  'a'
  'b'
  'B'
  'c'

julia> s = Set([NaN, 0.0, 1.0, 2.0]);

julia> -0.0 in s # isequal(0.0, -0.0) is false
false

julia> NaN in s # isequal(NaN, NaN) is true
true
```
