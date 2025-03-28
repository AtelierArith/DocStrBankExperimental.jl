```
invoke(f, argtypes::Type, args...; kwargs...)
```

Ruft eine Methode für die gegebene generische Funktion `f` auf, die den angegebenen Typen `argtypes` für die angegebenen Argumente `args` entspricht und die Schlüsselwortargumente `kwargs` übergibt. Die Argumente `args` müssen den angegebenen Typen in `argtypes` entsprechen, d.h. eine Umwandlung wird nicht automatisch durchgeführt. Diese Methode ermöglicht das Aufrufen einer Methode, die nicht die spezifischste übereinstimmende Methode ist, was nützlich ist, wenn das Verhalten einer allgemeineren Definition ausdrücklich benötigt wird (oft als Teil der Implementierung einer spezifischeren Methode derselben Funktion).

Seien Sie vorsichtig, wenn Sie `invoke` für Funktionen verwenden, die Sie nicht selbst geschrieben haben. Welche Definition für die gegebenen `argtypes` verwendet wird, ist ein Implementierungsdetail, es sei denn, die Funktion gibt ausdrücklich an, dass das Aufrufen mit bestimmten `argtypes` Teil der öffentlichen API ist. Zum Beispiel wird der Wechsel zwischen `f1` und `f2` im folgenden Beispiel normalerweise als kompatibel angesehen, da die Änderung für den Aufrufer bei einem normalen (nicht-`invoke`) Aufruf unsichtbar ist. Die Änderung ist jedoch sichtbar, wenn Sie `invoke` verwenden.

# Beispiele

```jldoctest
julia> f(x::Real) = x^2;

julia> f(x::Integer) = 1 + invoke(f, Tuple{Real}, x);

julia> f(2)
5

julia> f1(::Integer) = Integer
       f1(::Real) = Real;

julia> f2(x::Real) = _f2(x)
       _f2(::Integer) = Integer
       _f2(_) = Real;

julia> f1(1)
Integer

julia> f2(1)
Integer

julia> invoke(f1, Tuple{Real}, 1)
Real

julia> invoke(f2, Tuple{Real}, 1)
Integer
```
