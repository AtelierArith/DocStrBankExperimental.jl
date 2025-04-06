```
deepcopy(x)
```

Crea una copia profunda de `x`: todo se copia recursivamente, resultando en un objeto completamente independiente. Por ejemplo, hacer una copia profunda de un arreglo crea copias profundas de todos los objetos que contiene y produce un nuevo arreglo con la estructura de relación consistente (por ejemplo, si los dos primeros elementos son el mismo objeto en el arreglo original, los dos primeros elementos del nuevo arreglo también serán el mismo objeto `deepcopy`ed). Llamar a `deepcopy` en un objeto debería tener generalmente el mismo efecto que serializar y luego deserializarlo.

Aunque normalmente no es necesario, los tipos definidos por el usuario pueden anular el comportamiento predeterminado de `deepcopy` definiendo una versión especializada de la función `deepcopy_internal(x::T, dict::IdDict)` (que no debería usarse de otra manera), donde `T` es el tipo para el que se va a especializar, y `dict` lleva un registro de los objetos copiados hasta ahora dentro de la recursión. Dentro de la definición, `deepcopy_internal` debería usarse en lugar de `deepcopy`, y la variable `dict` debería actualizarse según sea apropiado antes de devolver.
