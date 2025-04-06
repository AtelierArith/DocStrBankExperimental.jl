```
Float32 <: AbstractFloat <: Real
```

32位浮点数类型（IEEE 754标准）。二进制格式为1个符号位，8个指数位，23个小数位。

科学计数法的指数应以小写`f`输入，因此`2f3 === 2.0f0 * 10^3 === Float32(2_000)`。对于数组字面量和推导式，元素类型可以在方括号之前指定：`Float32[1,4,9] == Float32[i^2 for i in 1:3]`。

另见 [`Inf32`](@ref), [`NaN32`](@ref), [`Float16`](@ref), [`exponent`](@ref), [`frexp`](@ref)。
