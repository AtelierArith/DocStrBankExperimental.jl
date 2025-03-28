```
x && y
```

Kurzschluss-Boolean-UND.

Siehe auch [`&`](@ref), den ternären Operator `? :` und den Handbuchabschnitt über [Kontrollfluss](@ref man-conditional-evaluation).

# Beispiele

```jldoctest
julia> x = 3;

julia> x > 1 && x < 10 && x isa Int
true

julia> x < 0 && error("erwartetes positives x")
false
```
