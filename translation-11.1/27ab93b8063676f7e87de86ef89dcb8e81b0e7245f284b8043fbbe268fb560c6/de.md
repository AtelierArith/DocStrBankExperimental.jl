```
withfaces(f, kv::Pair...)
withfaces(f, kvpair_itr)
```

Führt `f` mit `FACES``.current` aus, das vorübergehend durch null oder mehr `:name => val` Argumente `kv` oder `kvpair_itr`, das `kv`-Formwerte erzeugt, modifiziert wird.

`withfaces` wird allgemein über die Syntax `withfaces(kv...) do ... end` verwendet. Ein Wert von `nothing` kann verwendet werden, um vorübergehend ein Gesicht zurückzusetzen (wenn es gesetzt wurde). Wenn `withfaces` zurückkehrt, wurde das ursprüngliche `FACES``.current` wiederhergestellt.

# Beispiele

```jldoctest; setup = :(import StyledStrings: Face, withfaces)
julia> withfaces(:yellow => Face(foreground=:red), :green => :blue) do
           println(styled"{yellow:red} und {green:blue} gemischt ergeben {magenta:purple}")
       end
rot und blau gemischt ergeben lila
```
