```
gemmt(uplo, tA, tB, alpha, A, B)
```

[`uplo`](@ref stdlib-blas-uplo)で指定された`A*B`の下三角または上三角部分、または[`tA`](@ref stdlib-blas-trans)および`tB`に応じた他の3つのバリアントを返します。

!!! compat "Julia 1.11"
    `gemmt`は少なくともJulia 1.11を必要とします。

