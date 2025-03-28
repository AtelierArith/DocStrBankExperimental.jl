```
Timer(callback::Function, delay; interval = 0)
```

Crea un temporizador que ejecuta la función `callback` en cada expiración del temporizador.

Las tareas en espera se despiertan y la función `callback` se llama después de un retraso inicial de `delay` segundos, y luego se repite con el intervalo dado en segundos. Si `interval` es igual a `0`, el callback solo se ejecuta una vez. La función `callback` se llama con un solo argumento, el temporizador en sí. Detén un temporizador llamando a `close`. El `callback` puede seguir ejecutándose una vez más, si el temporizador ya ha expirado.

# Ejemplos

Aquí el primer número se imprime después de un retraso de dos segundos, luego los números siguientes se imprimen rápidamente.

```julia-repl
julia> begin
           i = 0
           cb(timer) = (global i += 1; println(i))
           t = Timer(cb, 2, interval=0.2)
           wait(t)
           sleep(0.5)
           close(t)
       end
1
2
3
```
