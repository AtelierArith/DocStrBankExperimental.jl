```
yield(t::Task, arg = nothing)
```

`schedule(t, arg); yield()`'in hızlı, adaletsiz zamanlama versiyonu olan bu fonksiyon, zamanlayıcıyı çağırmadan önce hemen `t`'ye geçiş yapar.
