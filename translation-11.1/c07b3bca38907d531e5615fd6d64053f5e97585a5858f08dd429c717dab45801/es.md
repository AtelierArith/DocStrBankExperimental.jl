```
atan(y)
atan(y, x)
```

Calcula la tangente inversa de `y` o `y/x`, respectivamente.

Para un argumento real, este es el ángulo en radianes entre el eje positivo *x* y el punto (1, *y*), devolviendo un valor en el intervalo $[-\pi/2, \pi/2]$.

Para dos argumentos, este es el ángulo en radianes entre el eje positivo *x* y el punto (*x*, *y*), devolviendo un valor en el intervalo $[-\pi, \pi]$. Esto corresponde a una función estándar [`atan2`](https://en.wikipedia.org/wiki/Atan2). Ten en cuenta que por convención `atan(0.0,x)` se define como $\pi$ y `atan(-0.0,x)` se define como $-\pi$ cuando `x < 0`.

Consulta también [`atand`](@ref) para grados.

# Ejemplos

```jldoctest
julia> rad2deg(atan(-1/√3))
-30.000000000000004

julia> rad2deg(atan(-1, √3))
-30.000000000000004

julia> rad2deg(atan(1, -√3))
150.0
```
