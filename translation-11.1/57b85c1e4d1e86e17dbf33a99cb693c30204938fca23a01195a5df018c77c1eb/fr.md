```
escape_raw_string(s::AbstractString, delim='"') -> AbstractString
escape_raw_string(io, s::AbstractString, delim='"')
```

Échappe une chaîne de caractères de la manière utilisée pour analyser les littéraux de chaîne bruts. Pour chaque caractère de guillemet double (`"`) dans la chaîne d'entrée `s` (ou `delim` si spécifié), cette fonction compte le nombre *n* de caractères de barre oblique inversée (`\`) précédents, puis augmente le nombre de barres obliques de *n* à 2*n*+1 (même pour *n* = 0). Elle double également une séquence de barres obliques à la fin de la chaîne.

Cette convention d'échappement est utilisée dans les chaînes brutes et d'autres littéraux de chaîne non standard. (Il se trouve également que c'est la convention d'échappement attendue par le runtime du compilateur Microsoft C/C++ lorsqu'il analyse une chaîne de ligne de commande dans le tableau argv[]).

Voir aussi [`escape_string`](@ref).
