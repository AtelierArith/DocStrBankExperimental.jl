```
Unicode.julia_chartransform(c::Union{Char,Integer})
```

Ordne das Unicode-Zeichen (`Char`) oder den Codepunkt (`Integer`) `c` dem entsprechenden "äquivalenten" Zeichen oder Codepunkt zu, gemäß der benutzerdefinierten Äquivalenz, die im Julia-Parser verwendet wird (neben der NFC-Normalisierung).

Zum Beispiel wird `'µ'` (U+00B5 Mikro) von Julias Parser als äquivalent zu `'μ'` (U+03BC Mu) behandelt, sodass `julia_chartransform` diese Transformation durchführt, während andere Zeichen unverändert bleiben:

```jldoctest
julia> Unicode.julia_chartransform('µ')
'μ': Unicode U+03BC (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> Unicode.julia_chartransform('x')
'x': ASCII/Unicode U+0078 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
```

`julia_chartransform` ist hauptsächlich nützlich, um an die [`Unicode.normalize`](@ref) Funktion übergeben zu werden, um die Normalisierung zu imitieren, die vom Julia-Parser verwendet wird:

```jldoctest
julia> s = "µö"
"µö"

julia> s2 = Unicode.normalize(s, compose=true, stable=true, chartransform=Unicode.julia_chartransform)
"μö"

julia> collect(s2)
2-element Vector{Char}:
 'μ': Unicode U+03BC (Kategorie Ll: Buchstabe, Kleinbuchstabe)
 'ö': Unicode U+00F6 (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> s2 == string(Meta.parse(s))
true
```

!!! compat "Julia 1.8"
    Diese Funktion wurde in Julia 1.8 eingeführt.

