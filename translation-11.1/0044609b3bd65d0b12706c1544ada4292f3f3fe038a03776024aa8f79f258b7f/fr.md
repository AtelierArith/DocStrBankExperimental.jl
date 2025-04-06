```
tempname(parent=tempdir(); cleanup=true) -> String
```

Génère un chemin de fichier temporaire. Cette fonction ne renvoie qu'un chemin ; aucun fichier n'est créé. Le chemin est susceptible d'être unique, mais cela ne peut pas être garanti en raison de la très faible possibilité que deux appels simultanés à `tempname` génèrent le même nom de fichier. Le nom est garanti de différer de tous les fichiers déjà existants au moment de l'appel à `tempname`.

Lorsqu'il est appelé sans arguments, le nom temporaire sera un chemin absolu vers un nom temporaire dans le répertoire temporaire du système tel que donné par `tempdir()`. Si un argument de répertoire `parent` est donné, le chemin temporaire sera dans ce répertoire à la place.

L'option `cleanup` contrôle si le processus tente de supprimer automatiquement le chemin renvoyé lorsque le processus se termine. Notez que la fonction `tempname` ne crée aucun fichier ou répertoire à l'emplacement renvoyé, donc il n'y a rien à nettoyer à moins que vous ne créiez un fichier ou un répertoire là-bas. Si vous le faites et que `cleanup` est `true`, il sera supprimé à la fin du processus.

!!! compat "Julia 1.4"
    Les arguments `parent` et `cleanup` ont été ajoutés dans 1.4. Avant Julia 1.4, le chemin `tempname` ne serait jamais nettoyé à la fin du processus.


!!! warning
    Cela peut entraîner des failles de sécurité si un autre processus obtient le même nom de fichier et crée le fichier avant que vous ne puissiez le faire. Ouvrez le fichier avec `JL_O_EXCL` si cela vous préoccupe. L'utilisation de [`mktemp()`](@ref) est également recommandée à la place.

