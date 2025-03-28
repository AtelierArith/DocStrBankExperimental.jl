```
task_local_storage(body, key, value)
```

Llama a la función `body` con un almacenamiento local de tareas modificado, en el cual `value` se asigna a `key`; el valor anterior de `key`, o la falta del mismo, se restaura después. Útil para emular el alcance dinámico.
