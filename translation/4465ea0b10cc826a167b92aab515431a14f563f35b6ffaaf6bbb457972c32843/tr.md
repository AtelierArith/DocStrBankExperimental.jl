```
MergeSort
```

Sıralama fonksiyonunun birleştirme sıralama algoritmasını kullanması gerektiğini belirtin. Birleştirme sıralaması, koleksiyonu alt koleksiyonlara böler ve her adımda her alt koleksiyonu sıralayarak tekrar birleştirir, ta ki tüm koleksiyon sıralı biçimde yeniden bir araya gelene kadar.

Özellikler:

  * *kararlı*: eşit karşılaştırılan öğelerin sıralamasını korur (örneğin, büyük/küçük harf farkı gözetmeyen bir harf sıralamasında "a" ve "A").
  * *yerinde değil* bellekte.
  * *böl ve fethet* sıralama stratejisi.
  * *büyük koleksiyonlar için iyi performans* gösterir ancak genellikle [`QuickSort`](@ref) kadar hızlı değildir.
