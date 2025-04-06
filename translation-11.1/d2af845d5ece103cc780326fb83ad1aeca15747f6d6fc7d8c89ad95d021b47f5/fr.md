```
Pipe()
```

Construit un objet Pipe non initialisé, spécialement pour la communication IO entre plusieurs processus.

L'extrémité appropriée du pipe sera automatiquement initialisée si l'objet est utilisé dans le lancement de processus. Cela peut être utile pour obtenir facilement des références dans des pipelines de processus, par exemple :

```
julia> err = Pipe()

# Après cela, `err` sera initialisé et vous pourrez lire `foo`'s
# stderr depuis le pipe `err`, ou passer `err` à d'autres pipelines.
julia> run(pipeline(pipeline(`foo`, stderr=err), `cat`), wait=false)

# Maintenant, détruisez la moitié écrite du pipe, afin que la moitié lue obtienne EOF
julia> closewrite(err)

julia> read(err, String)
"stderr messages"
```

Voir aussi [`Base.link_pipe!`](@ref).
