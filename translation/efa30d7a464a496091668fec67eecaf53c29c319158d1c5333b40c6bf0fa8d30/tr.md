```
sparse(I, J, V,[ m, n, combine])
```

`S` boyutları `m x n` olan seyrek bir matris oluşturur, böylece `S[I[k], J[k]] = V[k]`. `combine` fonksiyonu, tekrar eden değerleri birleştirmek için kullanılır. Eğer `m` ve `n` belirtilmemişse, bunlar sırasıyla `maximum(I)` ve `maximum(J)` olarak ayarlanır. Eğer `combine` fonksiyonu sağlanmamışsa, `combine` varsayılan olarak `+` olur, ancak `V`'nin elemanları Boolean ise `combine` varsayılan olarak `|` olur. `I`'nin tüm elemanları `1 <= I[k] <= m` koşulunu sağlamalıdır ve `J`'nin tüm elemanları `1 <= J[k] <= n` koşulunu sağlamalıdır. (`I`, `J`, `V`) içindeki sayısal sıfırlar yapısal sıfır olarak korunur; sayısal sıfırları atmak için [`dropzeros!`](@ref) kullanın.

Ek belgeler ve uzman bir sürücü için `SparseArrays.sparse!`'ya bakın.

# Örnekler

```jldoctest
julia> Is = [1; 2; 3];

julia> Js = [1; 2; 3];

julia> Vs = [1; 2; 3];

julia> sparse(Is, Js, Vs)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3
```
