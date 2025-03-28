```
eof(stream) -> Bool
```

Teste si un flux d'E/S est à la fin du fichier. Si le flux n'est pas encore épuisé, cette fonction bloquera pour attendre plus de données si nécessaire, puis renverra `false`. Il est donc toujours sûr de lire un octet après avoir vu `eof` renvoyer `false`. `eof` renverra `false` tant que des données mises en mémoire tampon sont encore disponibles, même si l'extrémité distante d'une connexion est fermée.

# Exemples

```jldoctest
julia> b = IOBuffer("my buffer");

julia> eof(b)
false

julia> seekend(b);

julia> eof(b)
true
```
