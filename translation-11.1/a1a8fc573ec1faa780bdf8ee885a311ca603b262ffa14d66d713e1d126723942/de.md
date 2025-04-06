```
precompile(f, argtypes::Tuple{Vararg{Any}}, m::Method)
```

Kompiliere eine spezifische Methode für die gegebenen Argumenttypen vor. Dies kann verwendet werden, um eine andere Methode vorzukompilieren als die, die normalerweise durch Dispatch gewählt werden würde, und somit `invoke` nachzuahmen.
