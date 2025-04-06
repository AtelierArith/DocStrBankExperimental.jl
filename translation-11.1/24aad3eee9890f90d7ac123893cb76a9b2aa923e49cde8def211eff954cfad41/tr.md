```
arg_isdir(f::Function, arg::AbstractString) -> f(arg)
```

`arg_isdir` fonksiyonu, `arg`'ın mevcut bir dizinin yolu olması gerektiğini (aksi takdirde bir hata oluşur) alır ve bu yolu `f`'ye geçirerek nihayetinde `f(arg)` sonucunu döndürür. Bu, kesinlikle `ArgTools` tarafından sunulan en az kullanışlı araçtır ve çoğunlukla `arg_mkdir` ile simetri sağlamak ve tutarlı hata mesajları vermek için var olmuştur.
