```
Threads.maxthreadid() -> Int
```

Obtiene un límite inferior en el número de hilos (a través de todos los grupos de hilos) disponibles para el proceso de Julia, con semántica de adquisición atómica. El resultado siempre será mayor o igual a [`threadid()`](@ref) así como `threadid(task)` para cualquier tarea que pudiste observar antes de llamar a `maxthreadid`.
