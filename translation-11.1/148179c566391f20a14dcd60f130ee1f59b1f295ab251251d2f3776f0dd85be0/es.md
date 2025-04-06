```
Printf.Format(format_str)
```

Crea un objeto de formato compatible con printf de C que se puede utilizar para formatear valores.

La entrada `format_str` puede incluir cualquier carácter de especificador de formato válido y modificadores.

Un objeto `Format` se puede pasar a `Printf.format(f::Format, args...)` para producir una cadena formateada, o `Printf.format(io::IO, f::Format, args...)` para imprimir la cadena formateada directamente en `io`.

Para mayor comodidad, se puede utilizar la forma de macro de cadena `Printf.format"..."` para construir un objeto `Printf.Format` en el momento de la expansión de la macro.

!!! compat "Julia 1.6"
    `Printf.Format` requiere Julia 1.6 o posterior.

