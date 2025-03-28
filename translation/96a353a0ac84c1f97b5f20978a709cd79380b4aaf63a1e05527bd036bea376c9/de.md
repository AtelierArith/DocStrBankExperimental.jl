```
uuid5(ns::UUID, name::String) -> UUID
```

Generiert einen Version 5 (namensraum- und domänenbasierten) universell eindeutigen Bezeichner (UUID), wie in RFC 4122 angegeben.

!!! compat "Julia 1.1"
    Diese Funktion erfordert mindestens Julia 1.1.


# Beispiele

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> u4 = uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")

julia> u5 = uuid5(u4, "julia")
UUID("2df91e3f-da06-5362-a6fe-03772f2e14c9")
```
