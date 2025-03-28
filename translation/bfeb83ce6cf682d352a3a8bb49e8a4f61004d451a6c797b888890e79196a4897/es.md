```
@__FILE__ -> String
```

Expande a una cadena con la ruta al archivo que contiene la llamada a la macro, o una cadena vacía si se evalúa con `julia -e <expr>`. Devuelve `nothing` si la macro no tenía información de origen del analizador. Alternativamente, consulta [`PROGRAM_FILE`](@ref).
