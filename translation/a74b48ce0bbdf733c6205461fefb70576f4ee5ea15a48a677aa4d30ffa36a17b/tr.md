```
Printf.format(f::Printf.Format, args...) => String
Printf.format(io::IO, f::Printf.Format, args...)
```

Verilen `args`'e bir printf format nesnesi `f` uygulayın ve biçimlendirilmiş dizeyi döndürün (1. yöntem) veya doğrudan bir `io` nesnesine yazdırın (2. yöntem). C `printf` desteği hakkında daha fazla bilgi için [`@printf`](@ref) bölümüne bakın.
