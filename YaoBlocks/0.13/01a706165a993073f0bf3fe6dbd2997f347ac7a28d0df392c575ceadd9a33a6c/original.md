```
shift(θ)
```

Create a [`ShiftGate`](@ref) with phase `θ`.

$$
\begin{pmatrix}
1 & 0\\
0 & e^{i\theta}
\end{pmatrix}
$$

### Examples

```jldoctest; setup=:(using YaoBlocks)
julia> shift(0.1)
shift(0.1)
```
