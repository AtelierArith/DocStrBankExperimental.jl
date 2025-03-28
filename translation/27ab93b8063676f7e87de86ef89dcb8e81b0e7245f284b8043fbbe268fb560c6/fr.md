```
withfaces(f, kv::Pair...)
withfaces(f, kvpair_itr)
```

Exécutez `f` avec `FACES``.current` temporairement modifié par zéro ou plusieurs arguments `:name => val` `kv`, ou `kvpair_itr` qui produit des valeurs au format `kv`.

`withfaces` est généralement utilisé via la syntaxe `withfaces(kv...) do ... end`. Une valeur de `nothing` peut être utilisée pour désactiver temporairement une face (si elle a été définie). Lorsque `withfaces` retourne, l'original `FACES``.current` a été restauré.

# Exemples

```jldoctest; setup = :(import StyledStrings: Face, withfaces)
julia> withfaces(:yellow => Face(foreground=:red), :green => :blue) do
           println(styled"{yellow:red} and {green:blue} mixed make {magenta:purple}")
       end
red and blue mixed make purple
```
