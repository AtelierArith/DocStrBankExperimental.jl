```
>>(B::BitVector, n) -> BitVector
```

Sağ bit kaydırma operatörü, `B >> n`. `n >= 0` için, sonuç `B`'nin elemanlarının `n` pozisyon ileri kaydırılmasıyla elde edilir ve `false` değerleriyle doldurulur. Eğer `n < 0` ise, elemanlar geriye kaydırılır. `B << -n` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> B = BitVector([true, false, true, false, false])
5-element BitVector:
 1
 0
 1
 0
 0

julia> B >> 1
5-element BitVector:
 0
 1
 0
 1
 0

julia> B >> -1
5-element BitVector:
 0
 1
 0
 0
 0
```
