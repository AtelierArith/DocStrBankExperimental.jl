```
Float64 <: AbstractFloat <: Real
```

64位浮点数类型（IEEE 754标准）。二进制格式为1个符号位，11个指数位，52个小数位。请参见[`bitstring`](@ref)，[`signbit`](@ref)，[`exponent`](@ref)，[`frexp`](@ref)和[`significand`](@ref)以访问各种位。

这是浮点字面量的默认值，`1.0 isa Float64`，以及许多操作，如`1/2, 2pi, log(2), range(0,90,length=4)`。与整数不同，这个默认值不会随着`Sys.WORD_SIZE`的变化而改变。

科学记数法的指数可以用`e`或`E`输入，因此`2e3 === 2.0E3 === 2.0 * 10^3`。这样做比`10^n`更受推荐，因为整数会溢出，因此`2.0 * 10^19 < 0`但`2e19 > 0`。

另请参见[`Inf`](@ref)，[`NaN`](@ref)，[`floatmax`](@ref)，[`Float32`](@ref)，[`Complex`](@ref)。
