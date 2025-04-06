```
MIME
```

Un tipo que representa un formato de datos estándar de internet. "MIME" significa "Extensiones de Correo de Internet Multipropósito", ya que el estándar se utilizó originalmente para describir archivos multimedia adjuntos a mensajes de correo electrónico.

Un objeto `MIME` se puede pasar como el segundo argumento a [`show`](@ref) para solicitar la salida en ese formato.

# Ejemplos

```jldoctest
julia> show(stdout, MIME("text/plain"), "hi")
"hi"
```
