```
invmod(n::Integer, T) where {T <: Base.BitInteger}
invmod(n::T) where {T <: Base.BitInteger}
```

计算类型为 `T` 的整数环中 `n` 的模逆，即模 `2^N`，其中 `N = 8*sizeof(T)`（例如，对于 `Int32`，`N = 32`）。换句话说，这些方法满足以下恒等式：

```
n * invmod(n) == 1
(n * invmod(n, T)) % T == 1
(n % T) * invmod(n, T) == 1
```

请注意，这里的 `*` 是整数环 `T` 中的模乘法。

将整数类型所隐含的模数作为显式值指定通常不方便，因为根据定义，模数太大而无法由该类型表示。

模逆的计算效率远高于一般情况，使用的算法在 https://arxiv.org/pdf/2204.04342.pdf 中进行了描述。

!!! compat "Julia 1.11"
    `invmod(n)` 和 `invmod(n, T)` 方法需要 Julia 1.11 或更高版本。

