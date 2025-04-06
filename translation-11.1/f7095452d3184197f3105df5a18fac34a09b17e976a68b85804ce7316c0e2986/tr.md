```
similar(storagetype, axes)
```

`storagetype` tarafından belirtilen türde, ancak son argümanla belirtilen `axes` ile benzer şekilde, başlatılmamış bir değiştirilebilir dizi oluşturur.

**Örnekler**:

```
similar(Array{Int}, axes(A))
```

`Array{Int}` gibi "davranan" bir dizi oluşturur (ve gerçekten de birinin arkasında olabilir), ancak `A` ile aynı şekilde indekslenir. Eğer `A` geleneksel indeksleme kullanıyorsa, bu `Array{Int}(undef, size(A))` ile aynı olacaktır, ancak `A` alışılmadık indeksleme kullanıyorsa, sonucun indeksleri `A` ile eşleşecektir.

```
similar(BitArray, (axes(A, 2),))
```

`A`'nın sütunlarının indeksleriyle eşleşen 1 boyutlu bir mantıksal dizi oluşturur.
