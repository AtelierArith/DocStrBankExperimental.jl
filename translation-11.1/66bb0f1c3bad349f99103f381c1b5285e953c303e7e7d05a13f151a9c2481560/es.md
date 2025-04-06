```
convert(T, x)
```

Convierte `x` a un valor del tipo `T`.

Si `T` es un tipo de [`Integer`](@ref), se generará un [`InexactError`](@ref) si `x` no es representable por `T`, por ejemplo, si `x` no es un valor entero, o está fuera del rango soportado por `T`.

# Ejemplos

```jldoctest
julia> convert(Int, 3.0)
3

julia> convert(Int, 3.5)
ERROR: InexactError: Int64(3.5)
Stacktrace:
[...]
```

Si `T` es un tipo de [`AbstractFloat`](@ref), entonces devolverá el valor más cercano a `x` representable por `T`. Inf se trata como una ulp mayor que `floatmax(T)` para fines de determinación del más cercano.

```jldoctest
julia> x = 1/3
0.3333333333333333

julia> convert(Float32, x)
0.33333334f0

julia> convert(BigFloat, x)
0.333333333333333314829616256247390992939472198486328125
```

Si `T` es un tipo de colección y `x` es una colección, el resultado de `convert(T, x)` puede hacer referencia a todo o parte de `x`.

```jldoctest
julia> x = Int[1, 2, 3];

julia> y = convert(Vector{Int}, x);

julia> y === x
true
```

Ver también: [`round`](@ref), [`trunc`](@ref), [`oftype`](@ref), [`reinterpret`](@ref).
