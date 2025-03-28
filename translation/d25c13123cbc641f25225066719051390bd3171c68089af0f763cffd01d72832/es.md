```
@goto name
```

`@goto name` salta incondicionalmente a la declaración en la ubicación [`@label name`](@ref).

`@label` y `@goto` no pueden crear saltos a diferentes declaraciones de nivel superior. Los intentos causan un error. Para seguir usando `@goto`, encierra `@label` y `@goto` en un bloque.
