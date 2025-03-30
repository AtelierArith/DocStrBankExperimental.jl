```
isidentifier(s) -> Bool
```

`s` sembolü veya dizesinin, Julia kodunda geçerli bir sıradan tanımlayıcı (ikili/ünary operatör değil) olarak ayrıştırılan karakterler içerip içermediğini döndürür; ayrıca [`Base.isoperator`](@ref) kısmına da bakabilirsiniz.

Julia, bir `Symbol` içinde herhangi bir karakter dizisine ( `\0`'lar hariç) izin verir ve makrolar, çevresindeki kodla isim çakışmasını önlemek için `#` içeren değişken adlarını otomatik olarak kullanır. Ayrıştırıcının bir değişkeni tanıyabilmesi için, sınırlı bir karakter seti kullanır (Unicode ile büyük ölçüde genişletilmiştir). `isidentifier()` bir sembolün geçerli karakterler içerip içermediğini doğrudan sorgulamayı mümkün kılar.

# Örnekler

```jldoctest
julia> Meta.isidentifier(:x), Meta.isidentifier("1x")
(true, false)
```
