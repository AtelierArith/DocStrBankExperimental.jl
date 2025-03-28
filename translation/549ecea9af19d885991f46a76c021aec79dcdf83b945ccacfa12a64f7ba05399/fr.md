```
Test.Error <: Test.Result
```

La condition de test n'a pas pu être évaluée en raison d'une exception, ou elle a été évaluée à quelque chose d'autre qu'un [`Bool`](@ref). Dans le cas de `@test_broken`, il est utilisé pour indiquer qu'un `Result` `Pass` inattendu s'est produit.
