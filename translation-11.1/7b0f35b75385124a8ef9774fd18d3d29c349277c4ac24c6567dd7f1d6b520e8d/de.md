```
@s_str -> SubstitutionString
```

Konstruiere eine Substitutionszeichenkette, die für reguläre Ausdrucksersetzungen verwendet wird. Innerhalb der Zeichenkette beziehen sich Sequenzen der Form `\N` auf die N-te Erfassungsgruppe im regulären Ausdruck, und `\g<groupname>` bezieht sich auf eine benannte Erfassungsgruppe mit dem Namen `groupname`.

# Beispiele

```jldoctest
julia> msg = "#Hello# from Julia";

julia> replace(msg, r"#(.+)# from (?<from>\w+)" => s"FROM: \g<from>; MESSAGE: \1")
"FROM: Julia; MESSAGE: Hello"
```
