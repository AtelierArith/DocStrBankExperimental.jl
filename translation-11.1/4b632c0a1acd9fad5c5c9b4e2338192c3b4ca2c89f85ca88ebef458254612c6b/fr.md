```
@distributed
```

Une boucle for parallèle en mémoire distribuée de la forme :

```
@distributed [réducteur] pour var = plage
    corps
fin
```

La plage spécifiée est partitionnée et exécutée localement sur tous les travailleurs. Dans le cas où une fonction réductrice optionnelle est spécifiée, `@distributed` effectue des réductions locales sur chaque travailleur avec une réduction finale sur le processus appelant.

Notez que sans fonction réductrice, `@distributed` s'exécute de manière asynchrone, c'est-à-dire qu'il génère des tâches indépendantes sur tous les travailleurs disponibles et retourne immédiatement sans attendre l'achèvement. Pour attendre l'achèvement, préfixez l'appel avec [`@sync`](@ref), comme suit :

```
@sync @distributed pour var = plage
    corps
fin
```
