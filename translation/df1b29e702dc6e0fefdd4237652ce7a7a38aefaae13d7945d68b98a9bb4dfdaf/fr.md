```
arg_read(f::Function, arg::ArgRead) -> f(arg_io)
```

La fonction `arg_read` accepte un argument `arg` qui peut être l'un de ceux-ci :

  * `AbstractString` : un chemin de fichier à ouvrir pour la lecture
  * `AbstractCmd` : une commande à exécuter, lisant à partir de sa sortie standard
  * `IO` : un handle IO ouvert à lire

Que le corps retourne normalement ou lance une erreur, un chemin qui est ouvert sera fermé avant de retourner de `arg_read` et un handle `IO` sera vidé mais pas fermé avant de retourner de `arg_read`.

Remarque : lors de l'ouverture d'un fichier, ArgTools passera `lock = false` à l'appel de fichier `open(...)`. Par conséquent, l'objet retourné par cette fonction ne doit pas être utilisé depuis plusieurs threads. Cette restriction peut être assouplie à l'avenir, ce qui ne casserait aucun code fonctionnel.
