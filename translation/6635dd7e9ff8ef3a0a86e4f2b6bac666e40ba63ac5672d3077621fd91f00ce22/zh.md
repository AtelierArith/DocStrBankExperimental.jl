不安全的指针操作与在 C11 和 C++23 中声明为 `_Atomic` 和 `std::atomic` 类型的指针的加载和存储是兼容的。如果不支持原子加载 Julia 类型 `T`，可能会抛出错误。

另请参见: [`unsafe_load`](@ref), [`unsafe_modify!`](@ref), [`unsafe_replace!`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref)
