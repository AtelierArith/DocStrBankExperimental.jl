```
Sys.username() -> String
```

Geçerli kullanıcı için kullanıcı adını döndürür. Kullanıcı adı belirlenemiyorsa veya boşsa, bu işlev bir hata fırlatır.

Bir ortam değişkeni aracılığıyla geçersiz kılınabilir bir kullanıcı adı almak için, örneğin `USER`, şunu kullanmayı düşünün:

```julia
user = get(Sys.username, ENV, "USER")
```

!!! compat "Julia 1.11"
    Bu işlev en az Julia 1.11 gerektirir.


Ayrıca [`homedir`](@ref) bakınız.
