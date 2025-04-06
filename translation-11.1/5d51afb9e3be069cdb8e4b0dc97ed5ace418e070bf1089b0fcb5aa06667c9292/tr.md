```
ordschur(F::GeneralizedSchur, select::Union{Vector{Bool},BitVector}) -> F::GeneralizedSchur
```

Bir matris çifti `(A, B) = (Q*S*Z', Q*T*Z')` için Genel Schur faktörizasyonu `F`'yi mantıksal dizi `select`'e göre yeniden sıralar ve bir GenelSchur nesnesi `F` döndürür. Seçilen özdeğerler, hem `F.S` hem de `F.T`'nin öncelikli diyagonalinde görünür ve sol ve sağ ortogonal/unitary Schur vektörleri de yeniden sıralanır, böylece `(A, B) = F.Q*(F.S, F.T)*F.Z'` hala geçerli kalır ve `A` ve `B`'nin genel özdeğerleri hala `F.α./F.β` ile elde edilebilir.
