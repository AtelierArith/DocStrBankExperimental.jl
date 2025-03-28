```
@distributed
```

Un bucle for paralelo de memoria distribuida de la forma:

```
@distributed [reducer] for var = range
    body
end
```

El rango especificado se particiona y se ejecuta localmente en todos los trabajadores. En caso de que se especifique una función reductor opcional, `@distributed` realiza reducciones locales en cada trabajador con una reducción final en el proceso que llama.

Tenga en cuenta que sin una función reductor, `@distributed` se ejecuta de manera asíncrona, es decir, genera tareas independientes en todos los trabajadores disponibles y devuelve inmediatamente sin esperar a que se complete. Para esperar a que se complete, prefije la llamada con [`@sync`](@ref), como:

```
@sync @distributed for var = range
    body
end
```
