"     get*test*counts(::AbstractTestSet) -> TestCounts

Fonction récursive qui compte le nombre de résultats de test de chaque type directement dans le testset, et totalise à travers les testsets enfants.

Les `AbstractTestSet` personnalisés doivent implémenter cette fonction pour que leurs totaux soient comptés et affichés avec `DefaultTestSet` également.

Si cela n'est pas implémenté pour un `TestSet` personnalisé, l'impression revient à signaler `x` pour les échecs et `?s` pour la durée.
