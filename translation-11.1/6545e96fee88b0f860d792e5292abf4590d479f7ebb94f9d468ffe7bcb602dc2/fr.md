```
arg_write(f::Function, arg::ArgWrite) -> arg
arg_write(f::Function, arg::Nothing) -> tempname()
```

La fonction `arg_read` accepte un argument `arg` qui peut être l'un de ceux-ci :

  * `AbstractString` : un chemin de fichier à ouvrir pour l'écriture
  * `AbstractCmd` : une commande à exécuter, écrivant dans son entrée standard
  * `IO` : un handle IO ouvert à écrire
  * `Nothing` : un chemin temporaire doit être écrit

Si le corps retourne normalement, un chemin qui est ouvert sera fermé à l'achèvement ; un argument de handle IO est laissé ouvert mais vidé avant le retour. Si l'argument est `nothing`, alors un chemin temporaire est ouvert pour l'écriture et fermé à l'achèvement, et le chemin est retourné par `arg_write`. Dans tous les autres cas, `arg` lui-même est retourné. C'est un modèle utile puisque vous pouvez retourner de manière cohérente ce qui a été écrit, que ce soit un argument passé ou non.

S'il y a une erreur lors de l'évaluation du corps, un chemin qui est ouvert par `arg_write` pour l'écriture sera supprimé, qu'il soit passé en tant que chaîne ou qu'il s'agisse d'un chemin temporaire généré lorsque `arg` est `nothing`.

Remarque : lors de l'ouverture d'un fichier, ArgTools passera `lock = false` à l'appel de fichier `open(...)`. Par conséquent, l'objet retourné par cette fonction ne doit pas être utilisé depuis plusieurs threads. Cette restriction pourrait être assouplie à l'avenir, ce qui ne casserait aucun code fonctionnel.
