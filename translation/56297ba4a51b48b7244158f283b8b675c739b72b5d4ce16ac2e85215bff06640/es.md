```
Base.@constprop configuración [ex]
```

Controla el modo de propagación de constantes interprocedimental para la función anotada.

Se admiten dos `configuraciones`:

  * `Base.@constprop :agresivo [ex]`: aplica la propagación de constantes de manera agresiva. Para un método donde el tipo de retorno depende del valor de los argumentos, esto puede generar mejores resultados de inferencia a costa de un tiempo de compilación adicional.
  * `Base.@constprop :ninguno [ex]`: desactiva la propagación de constantes. Esto puede reducir los tiempos de compilación para funciones que Julia de otro modo podría considerar dignas de propagación de constantes. Los casos comunes son para funciones con argumentos de tipo `Bool` o `Symbol` o argumentos de palabra clave.

`Base.@constprop` se puede aplicar inmediatamente antes de una definición de función o dentro de un cuerpo de función.

```julia
# anotar definición en forma larga
Base.@constprop :agresivo function longdef(x)
    ...
end

# anotar definición en forma corta
Base.@constprop :agresivo shortdef(x) = ...

# anotar función anónima que crea un bloque `do`
f() do
    Base.@constprop :agresivo
    ...
end
```

!!! compat "Julia 1.10"
    El uso dentro de un cuerpo de función requiere al menos Julia 1.10.

