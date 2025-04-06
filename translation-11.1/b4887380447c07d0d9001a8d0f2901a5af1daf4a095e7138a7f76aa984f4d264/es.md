```
sum(itr; [init])
```

Devuelve la suma de todos los elementos en una colección.

El tipo de retorno es `Int` para enteros con signo de menos del tamaño de palabra del sistema, y `UInt` para enteros sin signo de menos del tamaño de palabra del sistema. Para todos los demás argumentos, se encuentra un tipo de retorno común al que se promueven todos los argumentos.

El valor devuelto para `itr` vacío puede ser especificado por `init`. Debe ser la identidad aditiva (es decir, cero) ya que no está especificado si `init` se utiliza para colecciones no vacías.

!!! compat "Julia 1.6"
    El argumento clave `init` requiere Julia 1.6 o posterior.


Véase también: [`reduce`](@ref), [`mapreduce`](@ref), [`count`](@ref), [`union`](@ref).

# Ejemplos

```jldoctest
julia> sum(1:20)
210

julia> sum(1:20; init = 0.0)
210.0
```
