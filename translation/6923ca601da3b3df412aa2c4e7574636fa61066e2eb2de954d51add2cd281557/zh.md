`AbstractChar` 类型是 Julia 中所有字符实现的超类型。字符表示一个 Unicode 代码点，可以通过 [`codepoint`](@ref) 函数转换为整数，以获取代码点的数值，或从相同的整数构造。这些数值决定了字符如何与 `<` 和 `==` 进行比较，例如。新的 `T <: AbstractChar` 类型至少应定义一个 `codepoint(::T)` 方法和一个 `T(::UInt32)` 构造函数。

给定的 `AbstractChar` 子类型可能只能表示 Unicode 的一个子集，在这种情况下，从不支持的 `UInt32` 值转换可能会抛出错误。相反，内置的 [`Char`](@ref) 类型表示 Unicode 的 *超集*（以无损编码无效字节流），在这种情况下，将非 Unicode 值 *转换* 为 `UInt32` 会抛出错误。可以使用 [`isvalid`](@ref) 函数检查给定 `AbstractChar` 类型中哪些代码点是可表示的。

在内部，`AbstractChar` 类型可能使用多种编码。通过 `codepoint(char)` 的转换不会揭示这种编码，因为它始终返回字符的 Unicode 值。任何 `c::AbstractChar` 的 `print(io, c)` 产生的编码由 `io` 决定（所有内置 `IO` 类型均为 UTF-8），如有必要，通过转换为 `Char`。

相反，`write(io, c)` 可能会根据 `typeof(c)` 发出编码，而 `read(io, typeof(c))` 应该读取与 `write` 相同的编码。新的 `AbstractChar` 类型必须提供自己的 `write` 和 `read` 实现。
