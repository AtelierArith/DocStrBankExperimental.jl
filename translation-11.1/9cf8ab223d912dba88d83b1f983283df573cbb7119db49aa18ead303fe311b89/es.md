```
@test_logs [patrones_de_log...] [palabras_clave] expresión
```

Recoge una lista de registros de log generados por `expresión` usando `collect_test_logs`, verifica que coincidan con la secuencia `patrones_de_log`, y devuelve el valor de `expresión`. Las `palabras_clave` proporcionan un filtrado simple de los registros de log: la palabra clave `min_level` controla el nivel mínimo de log que se recogerá para la prueba, la palabra clave `match_mode` define cómo se realizará la coincidencia (el valor predeterminado `:all` verifica que todos los logs y patrones coincidan de manera par a par; usa `:any` para verificar que el patrón coincida al menos una vez en algún lugar de la secuencia).

El patrón de log más útil es una tupla simple de la forma `(nivel,mensaje)`. Se puede usar un número diferente de elementos de tupla para coincidir con otros metadatos de log, correspondientes a los argumentos que se pasan a `AbstractLogger` a través de la función `handle_message`: `(nivel,mensaje,módulo,grupo,id,archivo,línea)`. Los elementos que están presentes se emparejarán con los campos del registro de log usando `==` por defecto, con los casos especiales de que se pueden usar `Symbol`s para los niveles de log estándar, y `Regex`s en el patrón coincidirán con campos de cadena o Symbol usando `occursin`.

# Ejemplos

Considera una función que registra una advertencia y varios mensajes de depuración:

```
function foo(n)
    @info "Haciendo foo con n=$n"
    for i=1:n
        @debug "Iteración $i"
    end
    42
end
```

Podemos probar el mensaje de información usando

```
@test_logs (:info,"Haciendo foo con n=2") foo(2)
```

Si también quisiéramos probar los mensajes de depuración, estos deben habilitarse con la palabra clave `min_level`:

```
using Logging
@test_logs (:info,"Haciendo foo con n=2") (:debug,"Iteración 1") (:debug,"Iteración 2") min_level=Logging.Debug foo(2)
```

Si deseas probar que se generan algunos mensajes particulares mientras ignoras el resto, puedes establecer la palabra clave `match_mode=:any`:

```
using Logging
@test_logs (:info,) (:debug,"Iteración 42") min_level=Logging.Debug match_mode=:any foo(100)
```

El macro puede encadenarse con `@test` para también probar el valor devuelto:

```
@test (@test_logs (:info,"Haciendo foo con n=2") foo(2)) == 42
```

Si deseas probar la ausencia de advertencias, puedes omitir especificar patrones de log y establecer el `min_level` en consecuencia:

```
# prueba que la expresión no registra mensajes cuando el nivel del logger es warn:
@test_logs min_level=Logging.Warn @info("Alguna información") # pasa
@test_logs min_level=Logging.Warn @warn("Alguna información") # falla
```

Si deseas probar la ausencia de advertencias (o mensajes de error) en [`stderr`](@ref) que no son generados por `@warn`, consulta [`@test_nowarn`](@ref). ```
