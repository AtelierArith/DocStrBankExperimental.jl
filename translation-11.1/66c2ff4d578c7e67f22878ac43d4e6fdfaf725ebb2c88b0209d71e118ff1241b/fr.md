```
dump(x; maxdepth=8)
```

Montre chaque partie de la représentation d'une valeur. La profondeur de la sortie est tronquée à `maxdepth`.

# Exemples

```jldoctest
julia> struct MyStruct
           x
           y
       end

julia> x = MyStruct(1, (2,3));

julia> dump(x)
MyStruct
  x: Int64 1
  y: Tuple{Int64, Int64}
    1: Int64 2
    2: Int64 3

julia> dump(x; maxdepth = 1)
MyStruct
  x: Int64 1
  y: Tuple{Int64, Int64}
```
