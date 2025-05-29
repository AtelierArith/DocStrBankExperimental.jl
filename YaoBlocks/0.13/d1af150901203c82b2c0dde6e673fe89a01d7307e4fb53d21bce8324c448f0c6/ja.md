```
cleanup(entries::EntryTable; zero_threshold=0.0)
```

エントリテーブルをクリーンアップします。1) エントリをソートし、2) アイテムをマージし、3) ゼロをクリーンアップします。振幅が `zero_threshold` 以下の値はゼロと見なされます。

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
