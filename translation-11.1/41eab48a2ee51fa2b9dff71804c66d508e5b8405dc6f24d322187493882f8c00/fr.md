```
Timer(delay; interval = 0)
```

Créez un minuteur qui réveille les tâches en attente (en appelant [`wait`](@ref) sur l'objet minuteur).

Les tâches en attente sont réveillées après un délai initial d'au moins `delay` secondes, puis se répètent après qu'au moins `interval` secondes se soient écoulées à nouveau. Si `interval` est égal à `0`, le minuteur est déclenché une seule fois. Lorsque le minuteur est fermé (en appelant [`close`](@ref)), les tâches en attente sont réveillées avec une erreur. Utilisez [`isopen`](@ref) pour vérifier si un minuteur est toujours actif.

!!! note
    `interval` est sujet à l'accumulation de décalage temporel. Si vous avez besoin d'événements précis à un moment absolu particulier, créez un nouveau minuteur à chaque expiration avec la différence jusqu'au prochain moment calculée.


!!! note
    Un `Timer` nécessite des points de yield pour mettre à jour son état. Par exemple, `isopen(t::Timer)` ne peut pas être utilisé pour temporiser une boucle while non-yielding.

