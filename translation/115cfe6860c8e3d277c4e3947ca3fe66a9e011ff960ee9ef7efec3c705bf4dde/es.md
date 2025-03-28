```
uuid1([rng::AbstractRNG]) -> UUID
```

Genera un identificador único universal (UUID) de versión 1 (basado en el tiempo), según lo especificado por la RFC 4122. Tenga en cuenta que el ID de nodo se genera aleatoriamente (no identifica al host) de acuerdo con la sección 4.5 de la RFC.

El rng predeterminado utilizado por `uuid1` no es `Random.default_rng()` y se debe esperar que cada invocación de `uuid1()` sin un argumento devuelva un identificador único. Es importante destacar que las salidas de `uuid1` no se repiten incluso cuando se llama a `Random.seed!(seed)`. Actualmente (a partir de Julia 1.6), `uuid1` utiliza `Random.RandomDevice` como el rng predeterminado. Sin embargo, este es un detalle de implementación que puede cambiar en el futuro.

!!! compat "Julia 1.6"
    La salida de `uuid1` no depende de `Random.default_rng()` a partir de Julia 1.6.


# Ejemplos

```jldoctest; filter = r"[a-z0-9]{8}-([a-z0-9]{4}-){3}[a-z0-9]{12}"
julia> using Random

julia> rng = MersenneTwister(1234);

julia> uuid1(rng)
UUID("cfc395e8-590f-11e8-1f13-43a2532b2fa8")
```
