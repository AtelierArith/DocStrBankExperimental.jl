```
@everywhere [procs()] expr
```

Ejecuta una expresión bajo `Main` en todos los `procs`. Los errores en cualquiera de los procesos se recopilan en una [`CompositeException`](@ref) y se lanzan. Por ejemplo:

```
@everywhere bar = 1
```

definirá `Main.bar` en todos los procesos actuales. Cualquier proceso agregado más tarde (digamos con [`addprocs()`](@ref)) no tendrá la expresión definida.

A diferencia de [`@spawnat`](@ref), `@everywhere` no captura ninguna variable local. En su lugar, las variables locales se pueden transmitir utilizando interpolación:

```
foo = 1
@everywhere bar = $foo
```

El argumento opcional `procs` permite especificar un subconjunto de todos los procesos para que ejecuten la expresión.

Similar a llamar a `remotecall_eval(Main, procs, expr)`, pero con dos características adicionales:

```
- Las declaraciones `using` e `import` se ejecutan primero en el proceso que llama, para asegurar
  que los paquetes estén precompilados.
- La ruta del archivo fuente actual utilizada por `include` se propaga a otros procesos.
```
