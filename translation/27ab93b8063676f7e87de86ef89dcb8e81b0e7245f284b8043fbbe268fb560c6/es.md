```
withfaces(f, kv::Pair...)
withfaces(f, kvpair_itr)
```

Ejecuta `f` con `FACES``.current` temporalmente modificado por cero o más argumentos `:name => val` `kv`, o `kvpair_itr` que produce valores en forma de `kv`.

`withfaces` se utiliza generalmente a través de la sintaxis `withfaces(kv...) do ... end`. Un valor de `nothing` se puede usar para desactivar temporalmente una cara (si ha sido configurada). Cuando `withfaces` retorna, el original `FACES``.current` ha sido restaurado.

# Ejemplos

```jldoctest; setup = :(import StyledStrings: Face, withfaces)
julia> withfaces(:yellow => Face(foreground=:red), :green => :blue) do
           println(styled"{yellow:red} and {green:blue} mixed make {magenta:purple}")
       end
red and blue mixed make purple
```
