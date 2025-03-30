```
@nref N A indexexpr
```

`A[i_1, i_2, ...]` gibi ifadeler oluşturur. `indexexpr` ya bir iterasyon sembolü öneki ya da anonim fonksiyon ifadesi olabilir.

# Örnekler

```jldoctest
julia> @macroexpand Base.Cartesian.@nref 3 A i
:(A[i_1, i_2, i_3])
```
