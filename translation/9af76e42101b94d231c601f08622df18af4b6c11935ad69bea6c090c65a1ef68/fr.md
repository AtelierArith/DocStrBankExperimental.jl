```
unsafe_wrap(Array, pointer::Ptr{T}, dims; own = false)
```

Enveloppez un objet `Array` de Julia autour des données à l'adresse donnée par `pointer`, sans faire de copie. Le type d'élément du pointeur `T` détermine le type d'élément du tableau. `dims` est soit un entier (pour un tableau 1d) soit un tuple des dimensions du tableau. `own` spécifie en option si Julia doit prendre possession de la mémoire, en appelant `free` sur le pointeur lorsque le tableau n'est plus référencé.

Cette fonction est étiquetée "unsafe" car elle plantera si `pointer` n'est pas une adresse mémoire valide pour des données de la longueur demandée. Contrairement à [`unsafe_load`](@ref) et [`unsafe_store!`](@ref), le programmeur est également responsable de s'assurer que les données sous-jacentes ne sont pas accessibles par deux tableaux de types d'éléments différents, similaire à la règle d'aliasage strict en C.
