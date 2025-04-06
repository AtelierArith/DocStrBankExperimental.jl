```
isdone(itr, [state]) -> Union{Bool, Missing}
```

Cette fonction fournit un indice de chemin rapide pour l'achèvement de l'itérateur. Cela est utile pour les itérateurs avec état qui souhaitent éviter que des éléments soient consommés s'ils ne vont pas être exposés à l'utilisateur (par exemple, lors de la vérification de l'achèvement dans `isempty` ou `zip`).

Les itérateurs avec état qui souhaitent opter pour cette fonctionnalité doivent définir une méthode `isdone` qui renvoie vrai/faux en fonction de l'état de l'itérateur. Les itérateurs sans état n'ont pas besoin d'implémenter cette fonction.

Si le résultat est `missing`, les appelants peuvent continuer et calculer `iterate(x, state) === nothing` pour obtenir une réponse définitive.

Voir aussi [`iterate`](@ref), [`isempty`](@ref)
