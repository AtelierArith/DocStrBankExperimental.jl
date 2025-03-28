```
asyncmap(f, c...; ntasks=0, batch_size=nothing)
```

Utiliza múltiples tareas concurrentes para mapear `f` sobre una colección (o múltiples colecciones de igual longitud). Para múltiples argumentos de colección, `f` se aplica elemento por elemento.

`ntasks` especifica el número de tareas que se ejecutarán de forma concurrente. Dependiendo de la longitud de las colecciones, si `ntasks` no está especificado, se utilizarán hasta 100 tareas para el mapeo concurrente.

`ntasks` también se puede especificar como una función sin argumentos. En este caso, el número de tareas que se ejecutarán en paralelo se verifica antes de procesar cada elemento y se inicia una nueva tarea si el valor de `ntasks_func` es mayor que el número actual de tareas.

Si se especifica `batch_size`, la colección se procesa en modo por lotes. `f` debe ser una función que acepte un `Vector` de tuplas de argumentos y debe devolver un vector de resultados. El vector de entrada tendrá una longitud de `batch_size` o menos.

Los siguientes ejemplos destacan la ejecución en diferentes tareas al devolver el `objectid` de las tareas en las que se ejecuta la función de mapeo.

Primero, con `ntasks` indefinido, cada elemento se procesa en una tarea diferente.

```
julia> tskoid() = objectid(current_task());

julia> asyncmap(x->tskoid(), 1:5)
5-element Array{UInt64,1}:
 0x6e15e66c75c75853
 0x440f8819a1baa682
 0x9fb3eeadd0c83985
 0xebd3e35fe90d4050
 0x29efc93edce2b961

julia> length(unique(asyncmap(x->tskoid(), 1:5)))
5
```

Con `ntasks=2`, todos los elementos se procesan en 2 tareas.

```
julia> asyncmap(x->tskoid(), 1:5; ntasks=2)
5-element Array{UInt64,1}:
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94

julia> length(unique(asyncmap(x->tskoid(), 1:5; ntasks=2)))
2
```

Con `batch_size` definido, la función de mapeo necesita ser cambiada para aceptar un arreglo de tuplas de argumentos y devolver un arreglo de resultados. `map` se utiliza en la función de mapeo modificada para lograr esto.

```
julia> batch_func(input) = map(x->string("args_tuple: ", x, ", element_val: ", x[1], ", task: ", tskoid()), input)
batch_func (generic function with 1 method)

julia> asyncmap(batch_func, 1:5; ntasks=2, batch_size=2)
5-element Array{String,1}:
 "args_tuple: (1,), element_val: 1, task: 9118321258196414413"
 "args_tuple: (2,), element_val: 2, task: 4904288162898683522"
 "args_tuple: (3,), element_val: 3, task: 9118321258196414413"
 "args_tuple: (4,), element_val: 4, task: 4904288162898683522"
 "args_tuple: (5,), element_val: 5, task: 9118321258196414413"
```
