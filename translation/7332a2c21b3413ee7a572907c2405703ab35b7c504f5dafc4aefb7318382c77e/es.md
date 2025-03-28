```
methodswith(typ[, módulo o función]; supertypes::Bool=false])
```

Devuelve un array de métodos con un argumento de tipo `typ`.

El segundo argumento opcional restringe la búsqueda a un módulo o función particular (el valor predeterminado son todos los módulos de nivel superior).

Si la palabra clave `supertypes` es `true`, también devuelve argumentos con un tipo padre de `typ`, excluyendo el tipo `Any`.

Véase también: [`methods`](@ref). ```
