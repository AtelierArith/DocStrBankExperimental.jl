```
@boundscheck(blk)
```

Annotiert den Ausdruck `blk` als einen Bereichsprüfblock, der durch [`@inbounds`](@ref) ausgelassen werden kann.

!!! note
    Die Funktion, in der `@boundscheck` geschrieben ist, muss in ihren Aufrufer inline eingefügt werden, damit `@inbounds` Wirkung zeigt.


# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> @inline function g(A, i)
           @boundscheck checkbounds(A, i)
           return "accessing ($A)[$i]"
       end;

julia> f1() = return g(1:2, -1);

julia> f2() = @inbounds return g(1:2, -1);

julia> f1()
ERROR: BoundsError: Versuch, auf 2-elementigen UnitRange{Int64} bei Index [-1] zuzugreifen
Stacktrace:
 [1] throw_boundserror(::UnitRange{Int64}, ::Tuple{Int64}) at ./abstractarray.jl:455
 [2] checkbounds at ./abstractarray.jl:420 [inlined]
 [3] g at ./none:2 [inlined]
 [4] f1() at ./none:1
 [5] top-level scope

julia> f2()
"accessing (1:2)[-1]"
```

!!! warning
    Die `@boundscheck`-Annotation ermöglicht es Ihnen als Bibliotheksautor, sich dafür zu entscheiden, dass *anderer Code* Ihre Bereichsprüfungen mit [`@inbounds`](@ref) entfernen kann. Wie dort angemerkt, muss der Aufrufer überprüfen—unter Verwendung von Informationen, auf die er zugreifen kann—dass seine Zugriffe gültig sind, bevor er `@inbounds` verwendet. Zum Beispiel erfordert das Indizieren in Ihre [`AbstractArray`](@ref)-Unterklassen, dass die Indizes gegen ihre [`axes`](@ref) überprüft werden. Daher sollten `@boundscheck`-Annotationen nur zu einer [`getindex`](@ref) oder [`setindex!`](@ref)-Implementierung hinzugefügt werden, nachdem Sie sichergestellt haben, dass ihr Verhalten korrekt ist.

