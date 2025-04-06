```
count(
    pattern::Union{AbstractChar,AbstractString,AbstractPattern},
    string::AbstractString;
    overlap::Bool = false,
)
```

Gibt die Anzahl der Übereinstimmungen für `pattern` in `string` zurück. Dies entspricht dem Aufruf von `length(findall(pattern, string))`, ist jedoch effizienter.

Wenn `overlap=true`, dürfen die übereinstimmenden Sequenzen sich in den Indizes des ursprünglichen Strings überlappen, andernfalls müssen sie aus disjunkten Zeichenbereichen stammen.

!!! compat "Julia 1.3"
    Diese Methode erfordert mindestens Julia 1.3.


!!! compat "Julia 1.7"
    Die Verwendung eines Zeichens als Muster erfordert mindestens Julia 1.7.


# Beispiele

```jldoctest
julia> count('a', "JuliaLang")
2

julia> count(r"a(.)a", "cabacabac", overlap=true)
3

julia> count(r"a(.)a", "cabacabac")
2
```
