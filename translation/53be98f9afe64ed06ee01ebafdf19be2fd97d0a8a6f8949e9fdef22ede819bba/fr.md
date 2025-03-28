```
reset(::Event)
```

Réinitialise un [`Event`](@ref) dans un état non défini. Ensuite, tout appel futur à `wait` bloquera jusqu'à ce que [`notify`](@ref) soit appelé à nouveau.
