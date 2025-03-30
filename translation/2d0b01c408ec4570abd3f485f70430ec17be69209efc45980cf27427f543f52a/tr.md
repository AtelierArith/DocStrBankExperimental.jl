```
ffmerge!(repo::GitRepo, ann::GitAnnotated)
```

Mevcut HEAD'e hızlı birleştirme değişiklikleri. Bu, yalnızca `ann` tarafından belirtilen commit'in mevcut HEAD'den türetilmesi durumunda mümkündür (örneğin, yerel dal ucundan sadece ileri olan bir uzak daldan değişiklikler çekerken).
