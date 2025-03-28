```
isdone(itr, [state]) -> Union{Bool, Missing}
```

Esta función proporciona una pista de ruta rápida para la finalización del iterador. Esto es útil para iteradores con estado que desean evitar que los elementos sean consumidos si no van a ser expuestos al usuario (por ejemplo, al verificar si está terminado en `isempty` o `zip`).

Los iteradores con estado que desean optar por esta función deben definir un método `isdone` que devuelva verdadero/falso dependiendo de si el iterador ha terminado o no. Los iteradores sin estado no necesitan implementar esta función.

Si el resultado es `missing`, los llamadores pueden proceder a calcular `iterate(x, state) === nothing` para obtener una respuesta definitiva.

Véase también [`iterate`](@ref), [`isempty`](@ref)
