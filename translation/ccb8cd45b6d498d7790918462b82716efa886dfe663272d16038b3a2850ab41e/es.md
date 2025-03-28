```
names(x::Module; all::Bool = false, imported::Bool = false)
```

Obtiene un vector de los nombres públicos de un `Module`, excluyendo los nombres obsoletos. Si `all` es verdadero, entonces la lista también incluye nombres no públicos definidos en el módulo, nombres obsoletos y nombres generados por el compilador. Si `imported` es verdadero, entonces los nombres importados explícitamente de otros módulos también se incluyen. Los nombres se devuelven en orden alfabético.

Como un caso especial, todos los nombres definidos en `Main` se consideran "públicos", ya que no es idiomático marcar explícitamente los nombres de `Main` como públicos.

!!! note
    `sym ∈ names(SomeModule)` *no* implica `isdefined(SomeModule, sym)`. `names` devolverá símbolos marcados con `public` o `export`, incluso si no están definidos en el módulo.


Véase también: [`Base.isexported`](@ref), [`Base.ispublic`](@ref), [`Base.@locals`](@ref), [`@__MODULE__`](@ref).
