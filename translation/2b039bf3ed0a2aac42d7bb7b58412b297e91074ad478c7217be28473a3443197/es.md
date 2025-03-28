```
Semaphore(sem_size)
```

Crea un semáforo de conteo que permite como máximo `sem_size` adquisiciones en uso en cualquier momento. Cada adquisición debe ser emparejada con una liberación.

Esto proporciona un ordenamiento de memoria de adquisición y liberación en las llamadas de adquisición/liberación.
