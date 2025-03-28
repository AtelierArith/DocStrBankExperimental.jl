```
disable_sigint(f::Function)
```

Desactiva el controlador de Ctrl-C durante la ejecución de una función en la tarea actual, para llamar a código externo que puede llamar a código julia que no es seguro para interrupciones. Se pretende que se llame utilizando la sintaxis de bloque `do` de la siguiente manera:

```
disable_sigint() do
    # código no seguro para interrupciones
    ...
end
```

Esto no es necesario en hilos de trabajo (`Threads.threadid() != 1`) ya que la `InterruptException` solo se entregará al hilo maestro. Las funciones externas que no llaman a código julia o al tiempo de ejecución de julia desactivan automáticamente sigint durante su ejecución.
