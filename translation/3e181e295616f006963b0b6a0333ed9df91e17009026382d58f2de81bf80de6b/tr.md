```
arg_mkdir(f::Function, arg::AbstractString) -> arg
arg_mkdir(f::Function, arg::Nothing) -> mktempdir()
```

`arg_mkdir` fonksiyonu, `arg`'ın aşağıdakilerden biri olması gerektiğini belirtir:

  * zaten mevcut olan boş bir dizinin yolu,
  * bir dizin olarak oluşturulabilecek mevcut olmayan bir yol, veya
  * `nothing`, bu durumda geçici bir dizin oluşturulur.

Tüm durumlarda dizinin yolu döndürülür. Eğer `f(arg)` sırasında bir hata oluşursa, dizin orijinal durumuna döndürülür: eğer zaten mevcutsa ama boşsa, boşaltılacak; eğer mevcut değilse silinecektir.
