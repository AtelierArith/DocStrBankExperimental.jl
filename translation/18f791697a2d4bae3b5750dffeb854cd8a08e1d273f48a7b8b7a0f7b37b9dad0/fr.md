```
replaceproperty!(x, f::Symbol, expected, desired, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

Effectuez une opération de comparaison et d'échange sur `x.f` de `expected` à `desired`, par égal. La syntaxe `@atomicreplace x.f expected => desired` peut être utilisée à la place de la forme d'appel de fonction.

Voir aussi [`replacefield!`](@ref Core.replacefield!) [`setproperty!`](@ref Base.setproperty!), [`setpropertyonce!`](@ref Base.setpropertyonce!).
