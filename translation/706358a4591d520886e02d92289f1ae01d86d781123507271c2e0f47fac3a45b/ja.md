```
sqrt(A::AbstractMatrix)
```

もし `A` に負の実固有値がない場合、`A` の主行列平方根を計算します。つまり、$X^2 = A$ となる固有値が正の実部を持つ一意の行列 $X$ です。それ以外の場合は、非主平方根が返されます。

`A` が実対称行列またはエルミート行列である場合、その固有分解（[`eigen`](@ref)）を使用して平方根を計算します。このような行列に対して、丸め誤差のためにわずかに負に見える固有値 λ は、ゼロであるかのように扱われます。より正確には、すべての固有値が `≥ -rtol*(max |λ|)` である行列は半正定値として扱われ（エルミート平方根を生成）、負の固有値はゼロと見なされます。`rtol` は `sqrt` へのキーワード引数（エルミート/実対称の場合のみ）で、デフォルトは `size(A,1)` でスケーリングされた機械精度です。

それ以外の場合、平方根はBjörck-Hammarling法 [^BH83] によって決定され、複素シュール形式（[`schur`](@ref)）を計算し、その後三角因子の複素平方根を計算します。実平方根が存在する場合は、この方法の拡張 [^H87] が使用され、実シュール形式を計算し、その後準三角因子の実平方根を計算します。

[^BH83]: Åke Björck and Sven Hammarling, "A Schur method for the square root of a matrix", Linear Algebra and its Applications, 52-53, 1983, 127-140. [doi:10.1016/0024-3795(83)80010-X](https://doi.org/10.1016/0024-3795(83)80010-X)

[^H87]: Nicholas J. Higham, "Computing real square roots of a real matrix", Linear Algebra and its Applications, 88-89, 1987, 405-430. [doi:10.1016/0024-3795(87)90118-2](https://doi.org/10.1016/0024-3795(87)90118-2)

# 例

```jldoctest
julia> A = [4 0; 0 4]
2×2 Matrix{Int64}:
 4  0
 0  4

julia> sqrt(A)
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
