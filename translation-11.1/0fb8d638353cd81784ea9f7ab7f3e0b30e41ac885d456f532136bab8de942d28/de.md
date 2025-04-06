```
@test_deprecated [pattern] expression
```

Wenn `--depwarn=yes` gesetzt ist, teste, dass `expression` eine Abwertungswarnung ausgibt und gib den Wert von `expression` zurück. Der Lognachricht-String wird mit `pattern` verglichen, das standardmäßig auf `r"deprecated"i` gesetzt ist.

Wenn `--depwarn=no` gesetzt ist, gib einfach das Ergebnis der Ausführung von `expression` zurück. Wenn `--depwarn=error` gesetzt ist, überprüfe, dass eine ErrorException ausgelöst wird.

# Beispiele

```
# Abgewertet in julia 0.7
@test_deprecated num2hex(1)

# Der zurückgegebene Wert kann durch Verketten mit @test getestet werden:
@test (@test_deprecated num2hex(1)) == "0000000000000001"
```
