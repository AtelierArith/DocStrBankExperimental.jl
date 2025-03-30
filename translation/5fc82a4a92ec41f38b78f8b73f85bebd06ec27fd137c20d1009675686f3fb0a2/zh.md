```
eltype(type)
```

确定通过迭代给定 `type` 的集合生成的元素的类型。对于字典类型，这将是 `Pair{KeyType,ValType}`。为了方便起见，提供了定义 `eltype(x) = eltype(typeof(x))`，这样可以传递实例而不是类型。然而，接受类型参数的形式应该为新类型定义。

另请参见: [`keytype`](@ref), [`typeof`](@ref).

# 示例

```jldoctest
julia> eltype(fill(1f0, (2,2)))
Float32

julia> eltype(fill(0x1, (2,2)))
UInt8
```
