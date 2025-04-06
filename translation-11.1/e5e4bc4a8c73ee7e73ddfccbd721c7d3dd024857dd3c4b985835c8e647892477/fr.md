```
versioninfo(io::IO=stdout; verbose::Bool=false)
```

Imprime des informations sur la version de Julia en cours d'utilisation. La sortie est contrôlée par des arguments clés booléens :

  * `verbose` : imprimer toutes les informations supplémentaires

!!! warning
    La sortie de cette fonction peut contenir des informations sensibles. Avant de partager la sortie, veuillez la revoir et supprimer toute donnée qui ne devrait pas être partagée publiquement.


Voir aussi : [`VERSION`](@ref).
