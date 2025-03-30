```
addface!(name::Symbol => default::Face)
```

`name` ile yeni bir yüz oluşturun. Bu isimle zaten bir yüz mevcut değilse, `default` hem `FACES``.default`'a hem de (bir kopyası) `FACES`.`current`'a eklenir ve mevcut değer döndürülür.

Eğer `name` yüzü zaten mevcutsa, `nothing` döndürülür.

# Örnekler

```jldoctest; setup = :(import StyledStrings: Face, addface!)
julia> addface!(:mypkg_myface => Face(slant=:italic, underline=true))
Face (örnek)
         slant: italic
     underline: true
```
