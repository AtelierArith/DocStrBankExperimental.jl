```
init(; n::Integer, delay::Real)
```

Configura el `delay` entre las trazas de retorno (medido en segundos) y el número `n` de punteros de instrucción que se pueden almacenar por hilo. Cada puntero de instrucción corresponde a una sola línea de código; las trazas de retorno generalmente consisten en una larga lista de punteros de instrucción. Ten en cuenta que se utilizan 6 espacios para punteros de instrucción por traza de retorno para almacenar metadatos y dos marcadores de fin NULL. La configuración actual se puede obtener llamando a esta función sin argumentos, y cada uno se puede establecer de forma independiente utilizando palabras clave o en el orden `(n, delay)`.
