```
@simd
```

Anotar un bucle `for` para permitir que el compilador tome libertades adicionales para permitir el reordenamiento del bucle.

!!! warning
    Esta característica es experimental y podría cambiar o desaparecer en futuras versiones de Julia. El uso incorrecto de la macro `@simd` puede causar resultados inesperados.


El objeto iterado en un bucle `@simd for` debe ser un rango unidimensional. Al usar `@simd`, estás afirmando varias propiedades del bucle:

  * Es seguro ejecutar iteraciones en un orden arbitrario o superpuesto, con especial consideración para las variables de reducción.
  * Las operaciones de punto flotante sobre las variables de reducción pueden ser reordenadas o contraídas, lo que puede causar resultados diferentes que sin `@simd`.

En muchos casos, Julia puede vectorizar automáticamente los bucles internos sin el uso de `@simd`. Usar `@simd` le da al compilador un poco más de margen para hacerlo posible en más situaciones. En cualquier caso, tu bucle interno debe tener las siguientes propiedades para permitir la vectorización:

  * El bucle debe ser un bucle más interno.
  * El cuerpo del bucle debe ser código de línea recta. Por lo tanto, [`@inbounds`](@ref) es actualmente necesario para todos los accesos a arreglos. El compilador a veces puede convertir expresiones cortas `&&`, `||` y `?:` en código de línea recta si es seguro evaluar todos los operandos incondicionalmente. Considera usar la función [`ifelse`](@ref) en lugar de `?:` en el bucle si es seguro hacerlo.
  * Los accesos deben tener un patrón de paso y no pueden ser "gathers" (lecturas de índices aleatorios) o "scatters" (escrituras de índices aleatorios).
  * El paso debe ser un paso unitario.

!!! note
    El `@simd` no afirma por defecto que el bucle esté completamente libre de dependencias de memoria llevadas por el bucle, lo cual es una suposición que puede ser fácilmente violada en código genérico. Si estás escribiendo código no genérico, puedes usar `@simd ivdep for ... end` para también afirmar que:


  * No existen dependencias de memoria llevadas por el bucle.
  * Ninguna iteración espera nunca a que una iteración anterior avance.
