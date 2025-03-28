```
with(f::Function, obj)
```

Fonction d'aide à la gestion des ressources. Applique `f` à `obj`, en s'assurant d'appeler `close` sur `obj` après que `f` ait réussi à retourner ou ait levé une erreur. Garantit que les ressources git allouées sont finalisées dès qu'elles ne sont plus nécessaires.
