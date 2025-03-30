```
randsubseq([rng=default_rng(),] A, p) -> Vector
```

Verilen dizi `A`'nın rastgele bir alt dizisini içeren bir vektör döndürür; burada `A`'nın her bir elemanı bağımsız olasılık `p` ile (sırasıyla) dahil edilir. (Karmaşıklık `p*length(A)` cinsindendir, bu nedenle bu fonksiyon `p` küçük ve `A` büyük olsa bile etkilidir.) Teknik olarak, bu süreç `A`'nın "Bernoulli örneklemesi" olarak bilinir.

# Örnekler

```jldoctest
julia> randsubseq(Xoshiro(123), 1:8, 0.3)
2-element Vector{Int64}:
 4
 7
```
