```
fetch(;include_meta = true) -> data
```

Renvoie une copie du tampon des traces de profil. Notez que les valeurs dans `data` n'ont de signification que sur cette machine dans la session actuelle, car elles dépendent des adresses mémoire exactes utilisées dans la compilation JIT. Cette fonction est principalement destinée à un usage interne ; [`retrieve`](@ref) peut être un meilleur choix pour la plupart des utilisateurs. Par défaut, des métadonnées telles que threadid et taskid sont incluses. Définissez `include_meta` sur `false` pour supprimer les métadonnées.
