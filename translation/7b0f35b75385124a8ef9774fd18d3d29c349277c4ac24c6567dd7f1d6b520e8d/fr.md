```
@s_str -> SubstitutionString
```

Construit une chaîne de substitution, utilisée pour les substitutions d'expressions régulières. Dans la chaîne, les séquences de la forme `\N` font référence au N-ième groupe de capture dans l'expression régulière, et `\g<groupname>` fait référence à un groupe de capture nommé avec le nom `groupname`.

# Exemples

```jldoctest
julia> msg = "#Hello# from Julia";

julia> replace(msg, r"#(.+)# from (?<from>\w+)" => s"FROM: \g<from>; MESSAGE: \1")
"FROM: Julia; MESSAGE: Hello"
```
