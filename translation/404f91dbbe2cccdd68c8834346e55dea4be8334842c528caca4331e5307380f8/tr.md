```
applicable(f, args...) -> Bool
```

Verilen genel işlevin, verilen argümanlara uygulanabilir bir yöntemi olup olmadığını belirleyin.

Ayrıca bkz. [`hasmethod`](@ref).

# Örnekler

```jldoctest
julia> function f(x, y)
           x + y
       end;

julia> applicable(f, 1)
false

julia> applicable(f, 1, 2)
true
```
