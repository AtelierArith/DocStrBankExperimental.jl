```
ParserError
```

Type qui est retourné par [`tryparse`](@ref) et [`tryparsefile`](@ref) lorsque l'analyse échoue. Il contient (entre autres) les champs suivants :

  * `pos`, la position dans la chaîne lorsque l'erreur s'est produite
  * `table`, le résultat qui a jusqu'à présent été analysé avec succès
  * `type`, un type d'erreur, différent pour différents types d'erreurs
