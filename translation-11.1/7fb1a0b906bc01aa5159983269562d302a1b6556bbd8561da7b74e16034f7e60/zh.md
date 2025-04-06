```
Int
```

Sys.WORD_SIZE 位的有符号整数类型，`Int <: Signed <: Integer <: Real`。

这是大多数整数字面量的默认类型，并且是 `Int32` 或 `Int64` 的别名，具体取决于 `Sys.WORD_SIZE`。它是由诸如 [`length`](@ref) 的函数返回的类型，也是索引数组的标准类型。

请注意，整数在溢出时不会发出警告，因此 `typemax(Int) + 1 < 0` 和 `10^19 < 0`。可以通过使用 [`BigInt`](@ref) 来避免溢出。非常大的整数字面量将使用更宽的类型，例如 `10_000_000_000_000_000_000 isa Int128`。

整数除法是 [`div`](@ref) 别名 `÷`，而对整数执行的 [`/`](@ref) 返回 [`Float64`](@ref)。

另请参见 [`Int64`](@ref)，[`widen`](@ref)，[`typemax`](@ref)，[`bitstring`](@ref)。
