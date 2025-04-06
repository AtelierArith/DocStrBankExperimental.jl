```
Base.runtests(tests=["all"]; ncores=ceil(Int, Sys.CPU_THREADS / 2),
              exit_on_error=false, revise=false, [seed])
```

Ejecuta las pruebas unitarias de Julia listadas en `tests`, que pueden ser una cadena o un arreglo de cadenas, utilizando `ncores` procesadores. Si `exit_on_error` es `false`, cuando una prueba falla, todas las pruebas restantes en otros archivos aún se ejecutarán; de lo contrario, se descartan, cuando `exit_on_error == true`. Si `revise` es `true`, se utiliza el paquete `Revise` para cargar cualquier modificación a `Base` o a las bibliotecas estándar antes de ejecutar las pruebas. Si se proporciona una semilla a través del argumento de palabra clave, se utiliza para inicializar el generador de números aleatorios global en el contexto donde se ejecutan las pruebas; de lo contrario, la semilla se elige aleatoriamente.
