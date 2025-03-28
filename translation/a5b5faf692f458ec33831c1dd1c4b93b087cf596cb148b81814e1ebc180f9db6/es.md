```
Profile.Allocs.@profile [sample_rate=0.1] expr
```

Perfila las asignaciones que ocurren durante `expr`, devolviendo tanto el resultado como una estructura AllocResults.

Una tasa de muestreo de 1.0 registrará todo; 0.0 no registrará nada.

```julia
julia> Profile.Allocs.@profile sample_rate=0.01 peakflops()
1.03733270279065e11

julia> results = Profile.Allocs.fetch()

julia> last(sort(results.allocs, by=x->x.size))
Profile.Allocs.Alloc(Vector{Any}, Base.StackTraces.StackFrame[_new_array_ at array.c:127, ...], 5576)
```

Consulta el tutorial de perfilado en la documentación de Julia para más información.

!!! compat "Julia 1.11"
    Las versiones anteriores de Julia no podían capturar tipos en todos los casos. En versiones anteriores de Julia, si ves una asignación de tipo `Profile.Allocs.UnknownType`, significa que el perfilador no sabe qué tipo de objeto fue asignado. Esto sucedió principalmente cuando la asignación provenía de código generado producido por el compilador. Consulta [issue #43688](https://github.com/JuliaLang/julia/issues/43688) para más información.

    Desde Julia 1.11, todas las asignaciones deberían tener un tipo reportado.


!!! compat "Julia 1.8"
    El perfilador de asignaciones se agregó en Julia 1.8.

