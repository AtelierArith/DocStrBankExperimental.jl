```
one(x)
one(T::type)
```

`x` için çarpan kimliği döndürür: `one(x)*x == x*one(x) == x` eşitliğini sağlayan bir değer. Alternatif olarak, `one(T)` bir tür `T` alabilir; bu durumda `one`, türü `T` olan herhangi bir `x` için çarpan kimliği döndürür.

Mümkünse, `one(x)` `x` ile aynı türde bir değer döndürür ve `one(T)` türü `T` olan bir değer döndürür. Ancak, bu durum boyutlu nicelikleri temsil eden türler (örneğin, gün cinsinden zaman) için geçerli olmayabilir, çünkü çarpan kimliği boyutsuz olmalıdır. Bu durumda, `one(x)` `x` ile aynı hassasiyette (ve şekil, matrisler için) bir kimlik değeri döndürmelidir.

`x` ile aynı türde veya `T` türünde bir nicelik istiyorsanız, `oneunit`[@ref] yerine kullanın.

Ayrıca [`identity`](@ref) fonksiyonuna ve `I`'ye [`LinearAlgebra`](@ref man-linalg) içinde kimlik matrisine bakın.

# Örnekler

```jldoctest
julia> one(3.7)
1.0

julia> one(Int)
1

julia> import Dates; one(Dates.Day(1))
1
```
