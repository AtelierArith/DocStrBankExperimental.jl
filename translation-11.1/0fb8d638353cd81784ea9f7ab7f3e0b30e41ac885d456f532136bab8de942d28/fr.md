```
@test_deprecated [pattern] expression
```

Lorsque `--depwarn=yes`, testez que `expression` émet un avertissement de dépréciation et renvoyez la valeur de `expression`. La chaîne de message de journal sera comparée à `pattern`, qui par défaut est `r"deprecated"i`.

Lorsque `--depwarn=no`, renvoyez simplement le résultat de l'exécution de `expression`. Lorsque `--depwarn=error`, vérifiez qu'une ErrorException est levée.

# Exemples

```
# Déprécié dans julia 0.7
@test_deprecated num2hex(1)

# La valeur retournée peut être testée en chaînant avec @test :
@test (@test_deprecated num2hex(1)) == "0000000000000001"
```
