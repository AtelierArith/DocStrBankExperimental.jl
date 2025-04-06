```
ssh_known_hosts_files() :: Vector{String}
```

La fonction `ssh_known_hosts_files()` renvoie un vecteur de chemins des fichiers de hôtes connus SSH qui doivent être utilisés lors de l'établissement des identités des serveurs distants pour les connexions SSH. Par défaut, cette fonction renvoie

```
[joinpath(ssh_dir(), "known_hosts"), bundled_known_hosts]
```

où `bundled_known_hosts` est le chemin d'une copie d'un fichier d'hôtes connus qui est inclus avec ce package (contenant des clés d'hôtes connus pour `github.com` et `gitlab.com`). Si la variable d'environnement `SSH_KNOWN_HOSTS_FILES` est définie, sa valeur est cependant divisée en chemins sur le caractère `:` (ou sur `;` sous Windows) et ce vecteur de chemins est renvoyé à la place. Si un composant de ce vecteur est vide, il est étendu aux chemins d'hôtes connus par défaut.

Les packages qui utilisent `ssh_known_hosts_files()` devraient idéalement rechercher des entrées correspondantes en comparant le nom d'hôte et les types de clés, considérant la première entrée dans l'un des fichiers qui correspond comme étant l'identité définitive de l'hôte. Si l'appelant ne peut pas comparer le type de clé (par exemple, parce qu'il a été haché), il doit approximer l'algorithme ci-dessus en recherchant toutes les entrées correspondantes pour un hôte dans chaque fichier : si un fichier a des entrées pour un hôte, alors l'une d'elles doit correspondre ; l'appelant ne doit continuer à rechercher d'autres fichiers d'hôtes connus que s'il n'y a pas d'entrées pour l'hôte en question dans un fichier antérieur.
