```
Int8 <: Signed <: Integer
```

8位有符号整数类型。

表示数字 `n ∈ -128:127`。请注意，这种整数在溢出时不会发出警告，因此 `typemax(Int8) + Int8(1) < 0`。

另请参见 [`Int`](@ref Int64)、[`widen`](@ref)、[`BigInt`](@ref)。
