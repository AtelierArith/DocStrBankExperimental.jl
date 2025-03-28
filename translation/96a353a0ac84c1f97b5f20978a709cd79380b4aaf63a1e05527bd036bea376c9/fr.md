```
uuid5(ns::UUID, name::String) -> UUID
```

Génère un identifiant unique universel (UUID) de version 5 (basé sur l'espace de noms et le domaine), comme spécifié par la RFC 4122.

!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.


# Exemples

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> u4 = uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")

julia> u5 = uuid5(u4, "julia")
UUID("2df91e3f-da06-5362-a6fe-03772f2e14c9")
```
