```
public
```

`public` se utiliza dentro de los módulos para indicar a Julia qué nombres son parte de la API pública del módulo. Por ejemplo: `public foo` indica que el nombre `foo` es público, sin hacerlo disponible al [`using`](@ref) el módulo. Consulta la [sección del manual sobre módulos](@ref modules) para más detalles.

!!! compat "Julia 1.11"
    La palabra clave public se agregó en Julia 1.11. Antes de esto, la noción de publicidad era menos explícita.

