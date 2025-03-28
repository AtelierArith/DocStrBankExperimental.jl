```
record(ts::AbstractTestSet, res::Result)
```

Enregistre un résultat dans un ensemble de tests. Cette fonction est appelée par l'infrastructure `@testset` chaque fois qu'un macro `@test` contenu se termine, et reçoit le résultat du test (qui pourrait être une `Error`). Cela sera également appelé avec une `Error` si une exception est levée à l'intérieur du bloc de test mais en dehors d'un contexte `@test`.
