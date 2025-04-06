```
ordschur(F::Schur, select::Union{Vector{Bool},BitVector}) -> F::Schur
```

Bir matris `A = Z*T*Z'`'nin Schur faktorizasyonu `F`'yi mantıksal dizi `select`'e göre yeniden sıralar ve yeniden sıralanmış faktorizasyon `F` nesnesini döndürür. Seçilen özdeğerler `F.Schur`'un öncelikli diyagonalinde görünür ve `F.vectors`'ın karşılık gelen öncelikli sütunları, ilgili sağ invariyant alt uzayının ortogonal/unitary bir tabanını oluşturur. Gerçek durumda, bir karmaşık eşlenik özdeğer çifti ya her ikisi de dahil edilmeli ya da her ikisi de `select` aracılığıyla hariç tutulmalıdır.
