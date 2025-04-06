```
instances(T::Type)
```

Verilen türün tüm örneklerinin bir koleksiyonunu döndürür, eğer uygunsa. Genellikle sıralı türler için kullanılır (bkz. `@enum`).

# Örnekler

```jldoctest
julia> @enum Color red blue green

julia> instances(Color)
(red, blue, green)
```
