```
notify(condition, val=nothing; all=true, error=false)
```

Bir koşulu bekleyen görevleri uyandırın, onlara `val` geçirin. Eğer `all` `true` ise (varsayılan), bekleyen tüm görevler uyandırılır, aksi takdirde yalnızca biri uyandırılır. Eğer `error` `true` ise, geçirilen değer uyandırılan görevlerde bir istisna olarak yükseltilir.

Uyandırılan görevlerin sayısını döndürün. Eğer `condition` üzerinde bekleyen görev yoksa 0 döndürün.
