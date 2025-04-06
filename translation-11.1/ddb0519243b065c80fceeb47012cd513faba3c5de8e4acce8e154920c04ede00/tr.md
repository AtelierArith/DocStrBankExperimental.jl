```
global
```

`global x` mevcut kapsamda ve onun iç kapsamlarında `x`'in o isimdeki küresel değişkene referans vermesini sağlar. Daha fazla bilgi için [değişken kapsamı](@ref scope-of-variables) bölümüne bakın.

# Örnekler

```jldoctest
julia> z = 3
3

julia> function foo()
           global z = 6 # foo dışında tanımlanan z değişkenini kullan
       end
foo (generic function with 1 method)

julia> foo()
6

julia> z
6
```
