```
print_test_results(ts::AbstractTestSet, depth_pad=0)
```

Imprime les résultats d'un `AbstractTestSet` sous forme de tableau formaté.

`depth_pad` fait référence à la quantité de remplissage qui doit être ajoutée devant toute sortie.

Appelé à l'intérieur de `Test.finish`, si le testset `finish`é est le testset le plus haut.
