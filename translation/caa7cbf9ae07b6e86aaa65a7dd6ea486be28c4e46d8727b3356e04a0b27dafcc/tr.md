```
opnorm(A::AbstractMatrix, p::Real=2)
```

Vektör `p`-normu tarafından indüklenen operatör normunu (veya matris normunu) hesaplayın; burada geçerli `p` değerleri `1`, `2` veya `Inf`'dir. (Seyrek matrisler için, `p=2` şu anda uygulanmamıştır.) Frobenius normunu hesaplamak için [`norm`](@ref) kullanın.

`p=1` olduğunda, operatör normu `A`'nın maksimum mutlak sütun toplamıdır:

$$
\|A\|_1 = \max_{1 ≤ j ≤ n} \sum_{i=1}^m | a_{ij} |
$$

burada $a_{ij}$, $A$'nın elemanlarıdır ve $m$ ile $n$ onun boyutlarıdır.

`p=2` olduğunda, operatör normu spektral normdur ve `A`'nın en büyük tekil değerine eşittir.

`p=Inf` olduğunda, operatör normu `A`'nın maksimum mutlak satır toplamıdır:

$$
\|A\|_\infty = \max_{1 ≤ i ≤ m} \sum _{j=1}^n | a_{ij} |
$$

# Örnekler

```jldoctest
julia> A = [1 -2 -3; 2 3 -1]
2×3 Matrix{Int64}:
 1  -2  -3
 2   3  -1

julia> opnorm(A, Inf)
6.0

julia> opnorm(A, 1)
5.0
```
