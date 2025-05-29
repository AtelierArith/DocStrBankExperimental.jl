```
cleanup(entries::EntryTable; zero_threshold=0.0)
```

Clean up the entry table by 1) sort entries, 2) merge items and 3) clean up zeros. Any value with amplitude ≤ `zero_threshold` will be regarded as zero.

```jldoctest; setup=:(using Yao)
julia> et = EntryTable([bit"000",bit"011",bit"101",bit"101",bit"011",bit"110",bit"110",bit"011",], [1.0 + 0.0im,-1, 1,1,1,-1,1,1,-1])
EntryTable{DitStr{2, 3, Int64}, ComplexF64}:
  000 ₍₂₎   1.0 + 0.0im
  011 ₍₂₎   -1.0 + 0.0im
  101 ₍₂₎   1.0 + 0.0im
  101 ₍₂₎   1.0 + 0.0im
  011 ₍₂₎   1.0 + 0.0im
  110 ₍₂₎   -1.0 + 0.0im
  110 ₍₂₎   1.0 + 0.0im
  011 ₍₂₎   1.0 + 0.0im


julia> cleanup(et)
EntryTable{DitStr{2, 3, Int64}, ComplexF64}:
  000 ₍₂₎   1.0 + 0.0im
  011 ₍₂₎   1.0 + 0.0im
  101 ₍₂₎   2.0 + 0.0im
```
