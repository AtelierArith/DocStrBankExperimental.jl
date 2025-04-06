```
Profile.Allocs.@profile [sample_rate=0.1] expr
```

Profilez les allocations qui se produisent pendant `expr`, retournant à la fois le résultat et une structure AllocResults.

Un taux d'échantillonnage de 1.0 enregistrera tout ; 0.0 n'enregistrera rien.

```julia
julia> Profile.Allocs.@profile sample_rate=0.01 peakflops()
1.03733270279065e11

julia> results = Profile.Allocs.fetch()

julia> last(sort(results.allocs, by=x->x.size))
Profile.Allocs.Alloc(Vector{Any}, Base.StackTraces.StackFrame[_new_array_ at array.c:127, ...], 5576)
```

Voir le tutoriel de profilage dans la documentation Julia pour plus d'informations.

!!! compat "Julia 1.11"
    Les versions antérieures de Julia ne pouvaient pas capturer les types dans tous les cas. Dans les versions antérieures de Julia, si vous voyez une allocation de type `Profile.Allocs.UnknownType`, cela signifie que le profileur ne sait pas quel type d'objet a été alloué. Cela se produisait principalement lorsque l'allocation provenait de code généré par le compilateur. Voir [issue #43688](https://github.com/JuliaLang/julia/issues/43688) pour plus d'infos.

    Depuis Julia 1.11, toutes les allocations devraient avoir un type signalé.


!!! compat "Julia 1.8"
    Le profileur d'allocation a été ajouté dans Julia 1.8.

