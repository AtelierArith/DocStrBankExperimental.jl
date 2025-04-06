```
LAPACKException
```

Excepción genérica de LAPACK lanzada ya sea durante llamadas directas a las [funciones LAPACK](@ref man-linalg-lapack-functions) o durante llamadas a otras funciones que utilizan las funciones LAPACK internamente pero carecen de un manejo de errores especializado. El campo `info` contiene información adicional sobre el error subyacente y depende de la función LAPACK que fue invocada.
