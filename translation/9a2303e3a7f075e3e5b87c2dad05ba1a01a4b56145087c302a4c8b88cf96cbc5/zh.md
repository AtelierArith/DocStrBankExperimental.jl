```
hash(x[, h::UInt]) -> UInt
```

计算一个整数哈希码，使得 `isequal(x,y)` 意味着 `hash(x)==hash(y)`。可选的第二个参数 `h` 是另一个哈希码，用于与结果混合。

新类型应该实现两参数形式，通常通过递归调用两参数 `hash` 方法来混合内容的哈希与 `h`。通常，任何实现 `hash` 的类型也应该实现其自己的 [`==`](@ref)（因此 [`isequal`](@ref)），以保证上述属性。

当启动一个新的 Julia 进程时，哈希值可能会改变。

```jldoctest
julia> a = hash(10)
0x95ea2955abd45275

julia> hash(10, a) # 仅使用另一个哈希函数的输出作为第二个参数
0xd42bad54a8575b16
```

另请参见: [`objectid`](@ref), [`Dict`](@ref), [`Set`](@ref).
