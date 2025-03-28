```
Threads.atomic_fence()
```

Inserta una barrera de memoria de consistencia secuencial

Inserta una barrera de memoria con semánticas de orden de consistencia secuencial. Hay algoritmos donde esto es necesario, es decir, donde un orden de adquisición/liberación es insuficiente.

Es probable que esta sea una operación muy costosa. Dado que todas las demás operaciones atómicas en Julia ya tienen semánticas de adquisición/liberación, las barreras explícitas no deberían ser necesarias en la mayoría de los casos.

Para más detalles, consulta la instrucción `fence` de LLVM.
