```
<<(B::BitVector, n) -> BitVector
```

Sol bit kaydırma operatörü, `B << n`. `n >= 0` için, sonuç `B`'nin elemanları `n` pozisyon geri kaydırılarak, `false` değerleri ile doldurulmasıdır. Eğer `n < 0` ise, elemanlar ileri kaydırılır. `B >> -n` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> B = BitVector([true, false, true, false, false])
5-element BitVector:
 1
 0
 1
 0
 0

julia> B << 1
5-element BitVector:
 0
 1
 0
 0
 0

julia> B << -1
5-element BitVector:
 0
 1
 0
 1
 0
```
