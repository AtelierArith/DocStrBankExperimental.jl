```
GC.safepoint()
```

Inserta un punto en el programa donde puede ejecutarse la recolección de basura. Esto puede ser útil en casos raros en programas multihilo donde algunos hilos están asignando memoria (y por lo tanto pueden necesitar ejecutar GC) pero otros hilos están realizando solo operaciones simples (sin asignación, cambios de tarea o E/S). Llamar a esta función periódicamente en hilos que no asignan permite que la recolección de basura se ejecute.

!!! compat "Julia 1.4"
    Esta función está disponible a partir de Julia 1.4.

