```
retry(f;  delays=ExponentialBackOff(), check=nothing) -> Function
```

Renvoie une fonction anonyme qui appelle la fonction `f`. Si une exception se produit, `f` est appelée à nouveau, chaque fois que `check` renvoie `true`, après avoir attendu le nombre de secondes spécifié dans `delays`. `check` doit entrer l'état actuel de `delays` et l'`Exception`.

!!! compat "Julia 1.2"
    Avant Julia 1.2, cette signature était limitée à `f::Function`.


# Exemples

```julia
retry(f, delays=fill(5.0, 3))
retry(f, delays=rand(5:10, 2))
retry(f, delays=Base.ExponentialBackOff(n=3, first_delay=5, max_delay=1000))
retry(http_get, check=(s,e)->e.status == "503")(url)
retry(read, check=(s,e)->isa(e, IOError))(io, 128; all=false)
```
