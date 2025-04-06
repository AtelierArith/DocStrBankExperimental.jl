```
Printf.format(f::Printf.Format, args...) => String
Printf.format(io::IO, f::Printf.Format, args...)
```

Aplica un objeto de formato `f` a los argumentos proporcionados `args` y devuelve la cadena formateada (1ª método), o imprime directamente en un objeto `io` (2ª método). Consulta [`@printf`](@ref) para más detalles sobre el soporte de `printf` de C.
