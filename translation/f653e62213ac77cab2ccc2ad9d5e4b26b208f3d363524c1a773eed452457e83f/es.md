```
Char(c::Union{Number,AbstractChar})
```

`Char` es un tipo de 32 bits [`AbstractChar`](@ref) que es la representación predeterminada de caracteres en Julia. `Char` es el tipo utilizado para literales de caracteres como `'x'` y también es el tipo de elemento de [`String`](@ref).

Para representar de manera sin pérdida flujos de bytes arbitrarios almacenados en un `String`, un valor `Char` puede almacenar información que no se puede convertir a un punto de código Unicode; convertir tal `Char` a `UInt32` generará un error. La función [`isvalid(c::Char)`](@ref) se puede utilizar para consultar si `c` representa un carácter Unicode válido.
