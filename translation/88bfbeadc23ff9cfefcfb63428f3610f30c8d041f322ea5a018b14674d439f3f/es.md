```
puntero(array [, index])
```

Obtiene la dirección nativa de un array o cadena, opcionalmente en una ubicación dada `index`.

Esta función es "insegura". Ten cuidado de asegurarte de que una referencia de Julia a `array` exista mientras se use este puntero. El macro [`GC.@preserve`](@ref) debe ser utilizado para proteger el argumento `array` de la recolección de basura dentro de un bloque de código dado.

Llamar a [`Ref(array[, index])`](@ref Ref) es generalmente preferible a esta función ya que garantiza validez.
