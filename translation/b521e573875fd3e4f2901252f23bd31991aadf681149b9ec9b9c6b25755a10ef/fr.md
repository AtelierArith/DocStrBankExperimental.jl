```
count(
    pattern::Union{AbstractChar,AbstractString,AbstractPattern},
    string::AbstractString;
    overlap::Bool = false,
)
```

Retourne le nombre de correspondances pour `pattern` dans `string`. Cela équivaut à appeler `length(findall(pattern, string))` mais de manière plus efficace.

Si `overlap=true`, les séquences correspondantes sont autorisées à se chevaucher dans les indices de la chaîne d'origine, sinon elles doivent provenir de plages de caractères disjointes.

!!! compat "Julia 1.3"
    Cette méthode nécessite au moins Julia 1.3.


!!! compat "Julia 1.7"
    Utiliser un caractère comme motif nécessite au moins Julia 1.7.


# Exemples

```jldoctest
julia> count('a', "JuliaLang")
2

julia> count(r"a(.)a", "cabacabac", overlap=true)
3

julia> count(r"a(.)a", "cabacabac")
2
```
