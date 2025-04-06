```
ErrorException(msg)
```

Tipo de error genérico. El mensaje de error, en el campo `.msg`, puede proporcionar detalles más específicos.

# Ejemplos

```jldoctest
julia> ex = ErrorException("He hecho algo malo");

julia> ex.msg
"He hecho algo malo"
```
