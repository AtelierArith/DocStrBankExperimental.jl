```
Val(c)
```

`Val{c}()` döngü zamanı verisi içermez. Bu türler, `c` değerini kullanarak fonksiyonlar arasında bilgi geçişi yapmak için kullanılabilir; `c` bir `isbits` değeri veya bir `Symbol` olmalıdır. Bu yapının amacı, sabitler üzerinde doğrudan (derleme zamanında) dağıtım yapabilmektir; sabitin değerini döngü zamanında test etme gerekliliğini ortadan kaldırmaktır.

# Örnekler

```jldoctest
julia> f(::Val{true}) = "İyi"
f (generic function with 1 method)

julia> f(::Val{false}) = "Kötü"
f (generic function with 2 methods)

julia> f(Val(true))
"İyi"
```
