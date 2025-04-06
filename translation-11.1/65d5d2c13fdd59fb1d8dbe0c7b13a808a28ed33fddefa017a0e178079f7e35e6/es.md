```
tipo primitivo
```

`tipo primitivo` declara un tipo concreto cuyos datos consisten únicamente en una serie de bits. Ejemplos clásicos de tipos primitivos son los enteros y los valores de punto flotante. Algunas declaraciones de tipos primitivos incorporados como ejemplo:

```julia
tipo primitivo Char 32 fin
tipo primitivo Bool <: Integer 8 fin
```

El número después del nombre indica cuántos bits de almacenamiento requiere el tipo. Actualmente, solo se admiten tamaños que son múltiplos de 8 bits. La declaración [`Bool`](@ref) muestra cómo un tipo primitivo puede declararse opcionalmente como un subtipo de algún supertipo.
