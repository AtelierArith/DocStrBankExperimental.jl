```
setpropertyonce!(x, f::Symbol, value, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

Effectuez une opération de comparaison et d'échange sur `x.f` pour le définir sur `value` s'il n'était pas précédemment défini. La syntaxe `@atomiconce x.f = value` peut être utilisée à la place de la forme d'appel de fonction.

Voir aussi [`setfieldonce!`](@ref Core.replacefield!), [`setproperty!`](@ref Base.setproperty!), [`replaceproperty!`](@ref Base.replaceproperty!).

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.

