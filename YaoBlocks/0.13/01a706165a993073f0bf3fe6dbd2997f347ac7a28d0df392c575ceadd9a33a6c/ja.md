```
shift(θ)
```

位相 `θ` を持つ [`ShiftGate`](@ref) を作成します。

$$
\begin{pmatrix}
1 & 0\\
0 & e^{i\theta}
\end{pmatrix}
$$

### 例

```jldoctest; setup=:(using YaoBlocks)
julia> shift(0.1)
shift(0.1)
```
