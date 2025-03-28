```
apropos([io::IO=stdout], pattern::Union{AbstractString,Regex})
```

Busca las cadenas de documentación disponibles para las entradas que contienen `pattern`.

Cuando `pattern` es una cadena, se ignora el caso. Los resultados se imprimen en `io`.

`apropos` se puede llamar desde el modo de ayuda en el REPL envolviendo la consulta entre comillas dobles:

```
help?> "pattern"
```
