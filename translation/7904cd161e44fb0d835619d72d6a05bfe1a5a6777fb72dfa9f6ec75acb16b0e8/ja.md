```
isassigned(array, i) -> Bool
```

与えられた配列がインデックス `i` に関連付けられた値を持っているかどうかをテストします。インデックスが範囲外であるか、未定義の参照を持っている場合は `false` を返します。

# 例

```jldoctest
julia> isassigned(rand(3, 3), 5)
true

julia> isassigned(rand(3, 3), 3 * 3 + 1)
false

julia> mutable struct Foo end

julia> v = similar(rand(3), Foo)
3-element Vector{Foo}:
 #undef
 #undef
 #undef

julia> isassigned(v, 1)
false
```
