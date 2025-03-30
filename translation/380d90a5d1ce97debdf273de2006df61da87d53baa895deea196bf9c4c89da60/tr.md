```
@generated f
```

`@generated`, bir fonksiyonu oluşturmak için kullanılan bir anotasyondur. Oluşturulan fonksiyonun gövdesinde yalnızca argümanların türleri okunabilir (değerler değil). Fonksiyon, çağrıldığında değerlendirilen bir alıntı ifadesi döndürür. `@generated` makrosu, global kapsamı değiştiren veya değişken öğelere bağımlı olan fonksiyonlar üzerinde kullanılmamalıdır.

Daha fazla ayrıntı için [Metaprogramming](@ref) bölümüne bakın.

# Örnekler

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```
