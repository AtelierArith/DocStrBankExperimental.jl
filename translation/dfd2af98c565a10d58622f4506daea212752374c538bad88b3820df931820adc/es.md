```
BigFloat(x::Union{Real, AbstractString} [, rounding::RoundingMode=rounding(BigFloat)]; [precision::Integer=precision(BigFloat)])
```

Crea un número de punto flotante de precisión arbitraria a partir de `x`, con precisión `precision`. El argumento `rounding` especifica la dirección en la que el resultado debe ser redondeado si la conversión no se puede realizar exactamente. Si no se proporciona, estos se establecen por los valores globales actuales.

`BigFloat(x::Real)` es lo mismo que `convert(BigFloat,x)`, excepto si `x` ya es `BigFloat`, en cuyo caso devolverá un valor con la precisión establecida en la precisión global actual; `convert` siempre devolverá `x`.

`BigFloat(x::AbstractString)` es idéntico a [`parse`](@ref). Esto se proporciona por conveniencia ya que los literales decimales se convierten a `Float64` al ser analizados, por lo que `BigFloat(2.1)` puede no dar lo que esperas.

Véase también:

  * [`@big_str`](@ref)
  * [`rounding`](@ref) y [`setrounding`](@ref)
  * [`precision`](@ref) y [`setprecision`](@ref)

!!! compat "Julia 1.1"
    `precision` como un argumento de palabra clave requiere al menos Julia 1.1. En Julia 1.0 `precision` es el segundo argumento posicional (`BigFloat(x, precision)`).


# Ejemplos

```jldoctest
julia> BigFloat(2.1) # 2.1 aquí es un Float64
2.100000000000000088817841970012523233890533447265625

julia> BigFloat("2.1") # el BigFloat más cercano a 2.1
2.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> BigFloat("2.1", RoundUp)
2.100000000000000000000000000000000000000000000000000000000000000000000000000021

julia> BigFloat("2.1", RoundUp, precision=128)
2.100000000000000000000000000000000000007
```
