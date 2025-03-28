```
uuid4([rng::AbstractRNG]) -> UUID
```

Genera un identificador único universal (UUID) de versión 4 (aleatorio o pseudo-aleatorio), como se especifica en la RFC 4122.

El rng predeterminado utilizado por `uuid4` no es `Random.default_rng()` y se debe esperar que cada invocación de `uuid4()` sin un argumento devuelva un identificador único. Es importante destacar que las salidas de `uuid4` no se repiten incluso cuando se llama a `Random.seed!(seed)`. Actualmente (a partir de Julia 1.6), `uuid4` utiliza `Random.RandomDevice` como el rng predeterminado. Sin embargo, este es un detalle de implementación que puede cambiar en el futuro.

!!! compat "Julia 1.6"
    La salida de `uuid4` no depende de `Random.default_rng()` a partir de Julia 1.6.


# Ejemplos

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")
```
