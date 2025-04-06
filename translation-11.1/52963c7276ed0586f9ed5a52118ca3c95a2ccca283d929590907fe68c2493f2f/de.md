```
methods(f, [types], [module])
```

Gibt die Methodentabelle für `f` zurück.

Wenn `types` angegeben ist, wird ein Array von Methoden zurückgegeben, deren Typen übereinstimmen. Wenn `module` angegeben ist, wird ein Array von Methoden zurückgegeben, die in diesem Modul definiert sind. Eine Liste von Modulen kann auch als Array angegeben werden.

!!! compat "Julia 1.4"
    Mindestens Julia 1.4 ist erforderlich, um ein Modul anzugeben.


Siehe auch: [`which`](@ref), [`@which`](@ref Main.InteractiveUtils.@which) und [`methodswith`](@ref Main.InteractiveUtils.methodswith).
