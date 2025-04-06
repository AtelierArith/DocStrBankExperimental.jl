```
Profile.Allocs.@profile [sample_rate=0.1] expr
```

Profilieren Sie die Allokationen, die während `expr` stattfinden, und geben Sie sowohl das Ergebnis als auch eine AllocResults-Struktur zurück.

Eine Abtastrate von 1.0 erfasst alles; 0.0 erfasst nichts.

```julia
julia> Profile.Allocs.@profile sample_rate=0.01 peakflops()
1.03733270279065e11

julia> results = Profile.Allocs.fetch()

julia> last(sort(results.allocs, by=x->x.size))
Profile.Allocs.Alloc(Vector{Any}, Base.StackTraces.StackFrame[_new_array_ at array.c:127, ...], 5576)
```

Siehe das Profiling-Tutorial in der Julia-Dokumentation für weitere Informationen.

!!! compat "Julia 1.11"
    Ältere Versionen von Julia konnten in allen Fällen keine Typen erfassen. In älteren Versionen von Julia, wenn Sie eine Allokation des Typs `Profile.Allocs.UnknownType` sehen, bedeutet dies, dass der Profiler nicht weiß, welchen Typ von Objekt erfasst wurde. Dies geschah hauptsächlich, wenn die Allokation aus generiertem Code stammte, der vom Compiler erzeugt wurde. Siehe [issue #43688](https://github.com/JuliaLang/julia/issues/43688) für weitere Informationen.

    Seit Julia 1.11 sollten alle Allokationen einen gemeldeten Typ haben.


!!! compat "Julia 1.8"
    Der Allokationsprofiler wurde in Julia 1.8 hinzugefügt.

