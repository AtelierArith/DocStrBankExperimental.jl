```
CompositeException
```

Envuelve un `Vector` de excepciones lanzadas por una [`Task`](@ref) (por ejemplo, generadas por un trabajador remoto a través de un canal o una escritura de E/S local que se ejecuta de forma asíncrona o un trabajador remoto bajo `pmap`) con información sobre la serie de excepciones. Por ejemplo, si un grupo de trabajadores está ejecutando varias tareas y múltiples trabajadores fallan, el `CompositeException` resultante contendrá un "paquete" de información de cada trabajador que indica dónde y por qué ocurrieron las excepciones.
