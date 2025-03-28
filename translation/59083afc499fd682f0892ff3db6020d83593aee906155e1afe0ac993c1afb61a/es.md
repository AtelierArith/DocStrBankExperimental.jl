```
TaskLocalRNG
```

El `TaskLocalRNG` tiene un estado que es local a su tarea, no a su hilo. Se inicializa al crear la tarea, a partir del estado de su tarea padre, pero sin avanzar el estado del RNG del padre.

Como ventaja, el `TaskLocalRNG` es bastante rápido y permite simulaciones multihilo reproducibles (salvo condiciones de carrera), independientes de las decisiones del programador. Siempre que el número de hilos no se utilice para tomar decisiones sobre la creación de tareas, los resultados de la simulación también son independientes del número de hilos / CPUs disponibles. La secuencia aleatoria no debería depender de especificaciones de hardware, hasta el endianness y posiblemente el tamaño de palabra.

Usar o inicializar el RNG de cualquier otra tarea que no sea la devuelta por `current_task()` es un comportamiento indefinido: funcionará la mayor parte del tiempo y puede fallar silenciosamente en ocasiones.

Al inicializar `TaskLocalRNG()` con [`seed!`](@ref), la semilla pasada, si la hay, puede ser cualquier entero.

!!! compat "Julia 1.11"
    Inicializar `TaskLocalRNG()` con una semilla entera negativa requiere al menos Julia 1.11.


!!! compat "Julia 1.10"
    La creación de tareas ya no avanza el estado del RNG de la tarea padre a partir de Julia 1.10.

