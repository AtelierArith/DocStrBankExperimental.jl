```
uuid1([rng::AbstractRNG]) -> UUID
```

Génère un identifiant unique universel (UUID) de version 1 (basé sur le temps), comme spécifié par la RFC 4122. Notez que l'ID de nœud est généré aléatoirement (n'identifie pas l'hôte) conformément à la section 4.5 de la RFC.

Le rng par défaut utilisé par `uuid1` n'est pas `Random.default_rng()` et chaque invocation de `uuid1()` sans argument doit être attendue pour retourner un identifiant unique. Il est important de noter que les sorties de `uuid1` ne se répètent pas même lorsque `Random.seed!(seed)` est appelé. Actuellement (à partir de Julia 1.6), `uuid1` utilise `Random.RandomDevice` comme rng par défaut. Cependant, il s'agit d'un détail d'implémentation qui peut changer à l'avenir.

!!! compat "Julia 1.6"
    La sortie de `uuid1` ne dépend pas de `Random.default_rng()` à partir de Julia 1.6.


# Exemples

```jldoctest; filter = r"[a-z0-9]{8}-([a-z0-9]{4}-){3}[a-z0-9]{12}"
julia> using Random

julia> rng = MersenneTwister(1234);

julia> uuid1(rng)
UUID("cfc395e8-590f-11e8-1f13-43a2532b2fa8")
```
