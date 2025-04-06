```
RadioMenu
```

Un menú que permite a un usuario seleccionar una sola opción de una lista.

# Salida de Ejemplo

```julia-repl
julia> request(RadioMenu(options, pagesize=4))
Elige tu fruta favorita:
^  uva
   fresa
 > arándano
v  durazno
¡Tu fruta favorita es arándano!
```
