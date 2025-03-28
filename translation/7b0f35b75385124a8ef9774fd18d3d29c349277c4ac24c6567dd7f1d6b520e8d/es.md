```
@s_str -> SubstitutionString
```

Construye una cadena de sustitución, utilizada para sustituciones de expresiones regulares. Dentro de la cadena, las secuencias de la forma `\N` se refieren al N-ésimo grupo de captura en la regex, y `\g<groupname>` se refiere a un grupo de captura nombrado con el nombre `groupname`.

# Ejemplos

```jldoctest
julia> msg = "#Hello# from Julia";

julia> replace(msg, r"#(.+)# from (?<from>\w+)" => s"FROM: \g<from>; MESSAGE: \1")
"FROM: Julia; MESSAGE: Hello"
```
