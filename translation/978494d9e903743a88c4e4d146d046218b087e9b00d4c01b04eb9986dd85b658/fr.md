```
@simd
```

Annoter une boucle `for` pour permettre au compilateur de prendre des libertés supplémentaires pour permettre le réarrangement des boucles

!!! avertissement
    Cette fonctionnalité est expérimentale et pourrait changer ou disparaître dans de futures versions de Julia. Une utilisation incorrecte de la macro `@simd` peut entraîner des résultats inattendus.


L'objet itéré dans une boucle `@simd for` doit être une plage unidimensionnelle. En utilisant `@simd`, vous affirmez plusieurs propriétés de la boucle :

  * Il est sûr d'exécuter les itérations dans un ordre arbitraire ou qui se chevauche, avec une attention particulière pour les variables de réduction.
  * Les opérations en virgule flottante sur les variables de réduction peuvent être réorganisées ou contractées, ce qui peut entraîner des résultats différents de ceux sans `@simd`.

Dans de nombreux cas, Julia est capable de vectoriser automatiquement les boucles internes sans l'utilisation de `@simd`. L'utilisation de `@simd` donne au compilateur un peu plus de marge de manœuvre pour le rendre possible dans plus de situations. Dans tous les cas, votre boucle interne doit avoir les propriétés suivantes pour permettre la vectorisation :

  * La boucle doit être une boucle la plus interne
  * Le corps de la boucle doit être du code en ligne droite. Par conséquent, [`@inbounds`](@ref) est actuellement nécessaire pour tous les accès aux tableaux. Le compilateur peut parfois transformer de courtes expressions `&&`, `||` et `?:` en code en ligne droite s'il est sûr d'évaluer tous les opérandes de manière inconditionnelle. Envisagez d'utiliser la fonction [`ifelse`](@ref) au lieu de `?:` dans la boucle si cela est sûr à faire.
  * Les accès doivent avoir un motif de pas et ne peuvent pas être des "gather" (lectures à index aléatoire) ou des "scatter" (écritures à index aléatoire).
  * Le pas doit être un pas unitaire.

!!! note
    Le `@simd` n'affirme pas par défaut que la boucle est complètement exempte de dépendances de mémoire portées par la boucle, ce qui est une hypothèse qui peut facilement être violée dans du code générique. Si vous écrivez du code non générique, vous pouvez utiliser `@simd ivdep for ... end` pour affirmer également que :


  * Il n'existe aucune dépendance de mémoire portée par la boucle
  * Aucune itération n'attend jamais qu'une itération précédente progresse.
