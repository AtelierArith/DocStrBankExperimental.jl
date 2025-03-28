```
startswith(s::AbstractString, prefix::Regex)
```

Gibt `true` zurück, wenn `s` mit dem Regex-Muster `prefix` beginnt.

!!! note
    `startswith` kompiliert die Verankerung nicht in den regulären Ausdruck, sondern übergibt die Verankerung als `match_option` an PCRE. Wenn die Kompilierzeit amortisiert ist, ist `occursin(r"^...", s)` schneller als `startswith(s, r"...")`.


Siehe auch [`occursin`](@ref) und [`endswith`](@ref).

!!! compat "Julia 1.2"
    Diese Methode erfordert mindestens Julia 1.2.


# Beispiele

```jldoctest
julia> startswith("JuliaLang", r"Julia|Romeo")
true
```
