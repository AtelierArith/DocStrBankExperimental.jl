```
count([f=identity,] A::AbstractArray; dims=:)
```

`A`の要素のうち、`f`が`true`を返すものの数を指定された次元にわたってカウントします。

!!! compat "Julia 1.5"
    `dims`キーワードはJulia 1.5で追加されました。


!!! compat "Julia 1.6"
    `init`キーワードはJulia 1.6で追加されました。


# 例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> count(<=(2), A, dims=1)
1×2 Matrix{Int64}:
 1  1

julia> count(<=(2), A, dims=2)
2×1 Matrix{Int64}:
 2
 0
```
