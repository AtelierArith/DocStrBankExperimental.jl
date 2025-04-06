```
isequal(x, y) -> Bool
```

类似于 [`==`](@ref)，但在处理浮点数和缺失值时有所不同。`isequal` 将所有浮点 `NaN` 值视为相等，将 `-0.0` 视为不等于 `0.0`，并将 [`missing`](@ref) 视为等于 `missing`。始终返回一个 `Bool` 值。

`isequal` 是一种等价关系 - 它是自反的（`===` 意味着 `isequal`），对称的（`isequal(a, b)` 意味着 `isequal(b, a)`）和传递的（`isequal(a, b)` 和 `isequal(b, c)` 意味着 `isequal(a, c)`）。

# 实现

`isequal` 的默认实现调用 `==`，因此一个不涉及浮点值的类型通常只需要定义 `==`。

`isequal` 是哈希表（`Dict`）使用的比较函数。`isequal(x,y)` 必须意味着 `hash(x) == hash(y)`。

这通常意味着，对于存在自定义 `==` 或 `isequal` 方法的类型，必须实现相应的 [`hash`](@ref) 方法（反之亦然）。集合通常通过对所有内容递归调用 `isequal` 来实现 `isequal`。

此外，`isequal` 与 [`isless`](@ref) 相关联，它们共同定义了一个固定的全序关系，其中 `isequal(x, y)`、`isless(x, y)` 或 `isless(y, x)` 中恰好有一个必须为 `true`（其他两个为 `false`）。

标量类型通常不需要单独实现 `isequal`，除非它们表示的浮点数可以实现比作为通用后备提供的更高效的实现（基于 `isnan`、`signbit` 和 `==`）。

# 示例

```jldoctest
julia> isequal([1., NaN], [1., NaN])
true

julia> [1., NaN] == [1., NaN]
false

julia> 0.0 == -0.0
true

julia> isequal(0.0, -0.0)
false

julia> missing == missing
missing

julia> isequal(missing, missing)
true
```
