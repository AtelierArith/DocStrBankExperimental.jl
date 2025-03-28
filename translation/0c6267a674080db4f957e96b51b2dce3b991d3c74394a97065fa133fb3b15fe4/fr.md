```
seed!([rng=default_rng()], seed) -> rng
seed!([rng=default_rng()]) -> rng
```

Rensemence le générateur de nombres aléatoires : `rng` donnera une séquence de nombres reproductible si et seulement si un `seed` est fourni. Certains RNG n'acceptent pas de seed, comme `RandomDevice`. Après l'appel à `seed!`, `rng` est équivalent à un nouvel objet créé et initialisé avec le même seed. Les types de seeds acceptés dépendent du type de `rng`, mais en général, les seeds entiers devraient fonctionner.

Si `rng` n'est pas spécifié, il par défaut à la mise à jour de l'état du générateur local partagé.

# Exemples

```julia-repl
julia> Random.seed!(1234);

julia> x1 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> Random.seed!(1234);

julia> x2 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true

julia> rng = Xoshiro(1234); rand(rng, 2) == x1
true

julia> Xoshiro(1) == Random.seed!(rng, 1)
true

julia> rand(Random.seed!(rng), Bool) # pas reproductible
true

julia> rand(Random.seed!(rng), Bool) # pas reproductible non plus
false

julia> rand(Xoshiro(), Bool) # pas reproductible non plus
true
```
