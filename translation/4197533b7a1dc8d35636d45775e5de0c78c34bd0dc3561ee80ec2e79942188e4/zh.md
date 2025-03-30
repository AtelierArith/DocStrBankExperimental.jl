```
objectid(x) -> UInt
```

根据对象身份获取 `x` 的哈希值。

如果 `x === y`，则 `objectid(x) == objectid(y)`，通常当 `x !== y` 时，`objectid(x) != objectid(y)`。

另见 [`hash`](@ref)，[`IdDict`](@ref)。
