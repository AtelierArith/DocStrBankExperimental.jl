```
mktempdir(parent=tempdir(); prefix="jl_", cleanup=true) -> path
```

Crée un répertoire temporaire dans le répertoire `parent` avec un nom construit à partir du `prefix` donné et d'un suffixe aléatoire, et retourne son chemin. De plus, sur certaines plateformes, tout caractère `'X'` final dans `prefix` peut être remplacé par des caractères aléatoires. Si `parent` n'existe pas, une erreur est levée. L'option `cleanup` contrôle si le répertoire temporaire est automatiquement supprimé lorsque le processus se termine.

!!! compat "Julia 1.2"
    L'argument clé `prefix` a été ajouté dans Julia 1.2.


!!! compat "Julia 1.3"
    L'argument clé `cleanup` a été ajouté dans Julia 1.3. De manière connexe, à partir de 1.3, Julia supprimera les chemins temporaires créés par `mktempdir` lorsque le processus Julia se termine, sauf si `cleanup` est explicitement défini sur `false`.


Voir aussi : [`mktemp`](@ref), [`mkdir`](@ref).
