```
invokelatest(f, args...; kwargs...)
```

Appelle `f(args...; kwargs...)`, mais garantit que la méthode la plus récente de `f` sera exécutée. Cela est utile dans des circonstances spécialisées, par exemple dans des boucles d'événements de longue durée ou des fonctions de rappel qui peuvent appeler des versions obsolètes d'une fonction `f`. (L'inconvénient est que `invokelatest` est quelque peu plus lent que d'appeler `f` directement, et le type du résultat ne peut pas être inféré par le compilateur.)

!!! compat "Julia 1.9"
    Avant Julia 1.9, cette fonction n'était pas exportée et était appelée comme `Base.invokelatest`.

