```
methodswith(typ[, module ou fonction]; supertypes::Bool=false])
```

Renvoie un tableau de méthodes avec un argument de type `typ`.

Le deuxième argument optionnel restreint la recherche à un module ou une fonction particulière (la valeur par défaut est tous les modules de niveau supérieur).

Si le mot-clé `supertypes` est `true`, renvoie également les arguments avec un type parent de `typ`, en excluant le type `Any`.

Voir aussi : [`methods`](@ref).
