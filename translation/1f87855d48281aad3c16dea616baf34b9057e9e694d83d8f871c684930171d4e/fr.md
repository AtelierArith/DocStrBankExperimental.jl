```
IndexStyle(A)
IndexStyle(typeof(A))
```

`IndexStyle` spécifie le "style d'indexation natif" pour le tableau `A`. Lorsque vous définissez un nouveau type [`AbstractArray`](@ref), vous pouvez choisir d'implémenter soit l'indexation linéaire (avec [`IndexLinear`](@ref)) soit l'indexation cartésienne. Si vous décidez d'implémenter uniquement l'indexation linéaire, vous devez alors définir ce trait pour votre type de tableau :

```
Base.IndexStyle(::Type{<:MyArray}) = IndexLinear()
```

La valeur par défaut est [`IndexCartesian()`](@ref).

La machinerie d'indexation interne de Julia recalculera automatiquement (et de manière invisible) toutes les opérations d'indexation dans le style préféré. Cela permet aux utilisateurs d'accéder aux éléments de votre tableau en utilisant n'importe quel style d'indexation, même lorsque des méthodes explicites n'ont pas été fournies.

Si vous définissez les deux styles d'indexation pour votre `AbstractArray`, ce trait peut être utilisé pour sélectionner le style d'indexation le plus performant. Certaines méthodes vérifient ce trait sur leurs entrées et dispatchent vers différents algorithmes en fonction du modèle d'accès le plus efficace. En particulier, [`eachindex`](@ref) crée un itérateur dont le type dépend du paramètre de ce trait.
