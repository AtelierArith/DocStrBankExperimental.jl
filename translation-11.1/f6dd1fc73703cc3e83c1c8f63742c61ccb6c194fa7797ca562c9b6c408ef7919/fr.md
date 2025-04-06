```
uuid4([rng::AbstractRNG]) -> UUID
```

Génère un identifiant unique universel (UUID) de version 4 (aléatoire ou pseudo-aléatoire), comme spécifié par la RFC 4122.

Le rng par défaut utilisé par `uuid4` n'est pas `Random.default_rng()` et chaque invocation de `uuid4()` sans argument doit être attendue pour retourner un identifiant unique. Il est important de noter que les sorties de `uuid4` ne se répètent pas même lorsque `Random.seed!(seed)` est appelé. Actuellement (à partir de Julia 1.6), `uuid4` utilise `Random.RandomDevice` comme rng par défaut. Cependant, il s'agit d'un détail d'implémentation qui peut changer à l'avenir.

!!! compat "Julia 1.6"
    La sortie de `uuid4` ne dépend pas de `Random.default_rng()` à partir de Julia 1.6.


# Exemples

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")
```
