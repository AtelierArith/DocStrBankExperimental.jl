```
Base.isambiguous(m1, m2; ambiguous_bottom=false) -> Bool
```

Bestimmen Sie, ob zwei Methoden `m1` und `m2` für eine bestimmte Aufrufsignatur mehrdeutig sein könnten. Dieser Test wird im Kontext anderer Methoden derselben Funktion durchgeführt; isoliert könnten `m1` und `m2` mehrdeutig sein, aber wenn eine dritte Methode, die die Mehrdeutigkeit auflöst, definiert wurde, gibt dies `false` zurück. Alternativ könnten `m1` und `m2` isoliert geordnet sein, aber wenn eine dritte Methode nicht mit ihnen sortiert werden kann, könnten sie zusammen eine Mehrdeutigkeit verursachen.

Für parametrische Typen steuert das Schlüsselwortargument `ambiguous_bottom`, ob `Union{}` als mehrdeutige Schnittmenge von Typparametern zählt – wenn `true`, wird es als mehrdeutig betrachtet, wenn `false`, dann nicht.

# Beispiele

```jldoctest
julia> foo(x::Complex{<:Integer}) = 1
foo (generische Funktion mit 1 Methode)

julia> foo(x::Complex{<:Rational}) = 2
foo (generische Funktion mit 2 Methoden)

julia> m1, m2 = collect(methods(foo));

julia> typeintersect(m1.sig, m2.sig)
Tuple{typeof(foo), Complex{Union{}}}

julia> Base.isambiguous(m1, m2, ambiguous_bottom=true)
true

julia> Base.isambiguous(m1, m2, ambiguous_bottom=false)
false
```
