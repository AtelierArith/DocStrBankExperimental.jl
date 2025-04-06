```
GC.@preserve x1 x2 ... xn expr
```

Markiere die Objekte `x1, x2, ...` als *in Benutzung* während der Auswertung des Ausdrucks `expr`. Dies ist nur in unsicherem Code erforderlich, wo `expr` *implizit* Speicher oder andere Ressourcen verwendet, die einem der `x`s gehören.

*Implizite Nutzung* von `x` umfasst jede indirekte Nutzung von Ressourcen, die logisch von `x` besessen werden, die der Compiler nicht sehen kann. Einige Beispiele:

  * Zugriff auf den Speicher eines Objekts direkt über einen `Ptr`
  * Übergeben eines Zeigers auf `x` an `ccall`
  * Nutzung von Ressourcen von `x`, die im Finalizer bereinigt werden würden.

`@preserve` sollte im Allgemeinen keine Auswirkungen auf die Leistung in typischen Anwendungsfällen haben, in denen es die Lebensdauer des Objekts kurzzeitig verlängert. In der Implementierung hat `@preserve` Effekte wie den Schutz dynamisch zugewiesener Objekte vor der Garbage Collection.

# Beispiele

Beim Laden von einem Zeiger mit `unsafe_load` wird das zugrunde liegende Objekt implizit verwendet, zum Beispiel wird `x` implizit von `unsafe_load(p)` in folgendem Beispiel verwendet:

```jldoctest
julia> let
           x = Ref{Int}(101)
           p = Base.unsafe_convert(Ptr{Int}, x)
           GC.@preserve x unsafe_load(p)
       end
101
```

Beim Übergeben von Zeigern an `ccall` wird das darauf verwiesene Objekt implizit verwendet und sollte erhalten bleiben. (Beachte jedoch, dass du normalerweise `x` direkt an `ccall` übergeben solltest, was als explizite Nutzung zählt.)

```jldoctest
julia> let
           x = "Hello"
           p = pointer(x)
           Int(GC.@preserve x @ccall strlen(p::Cstring)::Csize_t)
           # Bevorzugte Alternative
           Int(@ccall strlen(x::Cstring)::Csize_t)
       end
5
```
