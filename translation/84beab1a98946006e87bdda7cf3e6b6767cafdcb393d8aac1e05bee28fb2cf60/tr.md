```
local
```

`local`, yeni bir yerel değişken tanımlar. Daha fazla bilgi için [değişken kapsamı üzerine kılavuz bölümüne](@ref scope-of-variables) bakın.

# Örnekler

```jldoctest
julia> function foo(n)
           x = 0
           for i = 1:n
               local x # döngüye özgü bir x tanımla
               x = i
           end
           x
       end
foo (generic function with 1 method)

julia> foo(10)
0
```
