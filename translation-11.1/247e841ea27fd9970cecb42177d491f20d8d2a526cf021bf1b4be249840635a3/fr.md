```
pointer_from_objref(x)
```

Obtenez l'adresse mémoire d'un objet Julia sous forme de `Ptr`. L'existence du `Ptr` résultant ne protégera pas l'objet de la collecte des ordures, vous devez donc vous assurer que l'objet reste référencé pendant toute la durée d'utilisation du `Ptr`.

Cette fonction ne peut pas être appelée sur des objets immuables, car ils n'ont pas d'adresses mémoire stables.

Voir aussi [`unsafe_pointer_to_objref`](@ref).
