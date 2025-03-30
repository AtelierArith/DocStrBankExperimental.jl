```
Int32 <: Signed <: Integer
```

32位有符号整数类型。

请注意，这种整数在溢出时不会发出警告，因此 `typemax(Int32) + Int32(1) < 0`。

另请参见 [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref)。
