```
@__FILE__ -> String
```

Développe en une chaîne avec le chemin vers le fichier contenant l'appel de macro, ou une chaîne vide si évalué par `julia -e <expr>`. Retourne `nothing` si la macro manquait d'informations sur la source du parseur. Voir alternativement [`PROGRAM_FILE`](@ref).
