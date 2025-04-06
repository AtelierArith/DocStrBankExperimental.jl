```
@isdefined s -> Bool
```

Überprüft, ob die Variable `s` im aktuellen Gültigkeitsbereich definiert ist.

Siehe auch [`isdefined`](@ref) für Feld Eigenschaften und [`isassigned`](@ref) für Array-Indizes oder [`haskey`](@ref) für andere Zuordnungen.

# Beispiele

```jldoctest
julia> @isdefined newvar
false

julia> newvar = 1
1

julia> @isdefined newvar
true

julia> function f()
           println(@isdefined x)
           x = 3
           println(@isdefined x)
       end
f (generische Funktion mit 1 Methode)

julia> f()
false
true
```
