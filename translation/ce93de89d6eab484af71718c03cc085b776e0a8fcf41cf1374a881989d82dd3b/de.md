```
endswith(s::AbstractString, suffix::Regex)
```

Gibt `true` zurück, wenn `s` mit dem Regex-Muster `suffix` endet.

!!! note
    `endswith` kompiliert die Verankerung nicht in den regulären Ausdruck, sondern übergibt die Verankerung als `match_option` an PCRE. Wenn die Kompilierzeit amortisiert ist, ist `occursin(r"...$", s)` schneller als `endswith(s, r"...")`.


Siehe auch [`occursin`](@ref) und [`startswith`](@ref).

!!! compat "Julia 1.2"
    Diese Methode erfordert mindestens Julia 1.2.


# Beispiele

```jldoctest
julia> endswith("JuliaLang", r"Lang|Roberts")
true
```
