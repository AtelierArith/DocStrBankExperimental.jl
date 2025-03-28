```
codeunits(s::AbstractString)
```

Obtenez un objet semblable à un vecteur contenant les unités de code d'une chaîne. Renvoie par défaut un wrapper `CodeUnits`, mais `codeunits` peut être défini en option pour de nouveaux types de chaînes si nécessaire.

# Exemples

```jldoctest
julia> codeunits("Juλia")
6-element Base.CodeUnits{UInt8, String}:
 0x4a
 0x75
 0xce
 0xbb
 0x69
 0x61
```
