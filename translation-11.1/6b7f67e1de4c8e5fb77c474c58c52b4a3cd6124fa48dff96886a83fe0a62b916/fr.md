```
TestCounts
```

Contient l'état pour rassembler de manière récursive les résultats d'un ensemble de tests à des fins d'affichage.

Champs :

  * `customized` : Indique si la fonction `get_test_counts` a été personnalisée pour l'`AbstractTestSet` pour lequel cet objet de comptage est destiné. Si une méthode personnalisée a été définie, passez toujours `true` au constructeur.
  * `passes` : Le nombre d'invocations `@test` réussies.
  * `fails` : Le nombre d'invocations `@test` échouées.
  * `errors` : Le nombre d'invocations `@test` avec erreurs.
  * `broken` : Le nombre d'invocations `@test` cassées.
  * `passes` : Le nombre cumulatif d'invocations `@test` réussies.
  * `fails` : Le nombre cumulatif d'invocations `@test` échouées.
  * `errors` : Le nombre cumulatif d'invocations `@test` avec erreurs.
  * `broken` : Le nombre cumulatif d'invocations `@test` cassées.
  * `duration` : La durée totale pendant laquelle l'`AbstractTestSet` en question a été exécuté, sous forme de `String` formatée.
