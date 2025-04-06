```
with_warn(f::Function, ::Type{T}, args...)
```

Fonction d'aide à la gestion des ressources. Applique `f` à `args`, en construisant d'abord une instance de type `T` à partir de `args`. S'assure d'appeler `close` sur l'objet résultant après que `f` ait réussi à retourner ou ait levé une erreur. Garantit que les ressources git allouées sont finalisées dès qu'elles ne sont plus nécessaires. Si une erreur est levée par `f`, un avertissement est affiché contenant l'erreur.
