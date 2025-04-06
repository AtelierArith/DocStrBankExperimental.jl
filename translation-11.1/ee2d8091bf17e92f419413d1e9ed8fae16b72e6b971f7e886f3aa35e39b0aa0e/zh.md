# SIMD Support

类型 `VecElement{T}` 旨在构建 SIMD 操作的库。实际使用它需要使用 `llvmcall`。该类型定义为：

```julia
struct VecElement{T}
    value::T
end
```

它有一个特殊的编译规则：当 `T` 是原始位类型时，同质元组 `VecElement{T}` 映射到 LLVM `vector` 类型。

在 `-O3` 下，编译器 *可能* 会自动对这样的元组进行向量化操作。例如，以下程序在使用 `julia -O3` 编译时，会在 x86 系统上生成两个 SIMD 加法指令 (`addps`)：

```julia
const m128 = NTuple{4,VecElement{Float32}}

function add(a::m128, b::m128)
    (VecElement(a[1].value+b[1].value),
     VecElement(a[2].value+b[2].value),
     VecElement(a[3].value+b[3].value),
     VecElement(a[4].value+b[4].value))
end

triple(c::m128) = add(add(c,c),c)

code_native(triple,(m128,))
```

然而，由于无法依赖自动向量化，未来的使用主要将通过使用 `llvmcall` 的库进行。
