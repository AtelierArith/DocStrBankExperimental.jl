```
dump(x; maxdepth=8)
```

Zeigt jeden Teil der Darstellung eines Wertes an. Die Tiefe der Ausgabe wird auf `maxdepth` gekürzt.

# Beispiele

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
