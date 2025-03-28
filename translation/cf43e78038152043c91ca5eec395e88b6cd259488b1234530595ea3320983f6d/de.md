# [Performance Tips](@id man-performance-tips)

In den folgenden Abschnitten gehen wir kurz auf einige Techniken ein, die dazu beitragen können, dass Ihr Julia-Code so schnell wie möglich läuft.

## Performance critical code should be inside a function

Jeder Code, der leistungs kritisch ist, sollte in einer Funktion sein. Code innerhalb von Funktionen läuft in der Regel viel schneller als Code auf der obersten Ebene, aufgrund der Funktionsweise des Compilers von Julia.

Die Verwendung von Funktionen ist nicht nur wichtig für die Leistung: Funktionen sind wiederverwendbarer und testbarer und verdeutlichen, welche Schritte unternommen werden und was ihre Eingaben und Ausgaben sind, [Write functions, not just scripts](@ref) ist auch eine Empfehlung des Julia Styleguides.

Die Funktionen sollten Argumente entgegennehmen, anstatt direkt auf globale Variablen zuzugreifen, siehe den nächsten Punkt.

## Avoid untyped global variables

Der Wert einer untypisierten globalen Variablen kann sich jederzeit ändern, was möglicherweise zu einer Änderung ihres Typs führt. Dies erschwert es dem Compiler, Code, der globale Variablen verwendet, zu optimieren. Dies gilt auch für typisierte Variablen, d.h. Typalias auf globaler Ebene. Variablen sollten lokal sein oder, wenn möglich, als Argumente an Funktionen übergeben werden.

Wir stellen fest, dass globale Namen häufig Konstanten sind, und sie als solche zu deklarieren, verbessert die Leistung erheblich:

```julia
const DEFAULT_VAL = 0
```

Wenn ein globaler Wert immer vom gleichen Typ ist, [the type should be annotated](@ref man-typed-globals).

Die Verwendung von untypisierten Globals kann optimiert werden, indem ihre Typen an der Stelle der Verwendung annotiert werden:

```julia
global x = rand(1000)

function loop_over_global()
    s = 0.0
    for i in x::Vector{Float64}
        s += i
    end
    return s
end
```

Das Übergeben von Argumenten an Funktionen ist der bessere Stil. Es führt zu wiederverwendbarerem Code und macht die Eingaben und Ausgaben klarer.

!!! note
    Alle Codes im REPL werden im globalen Kontext ausgewertet, sodass eine auf oberster Ebene definierte und zugewiesene Variable eine **globale** Variable sein wird. Variablen, die im oberen Bereich von Modulen definiert sind, sind ebenfalls global.


In der folgenden REPL-Sitzung:

```julia-repl
julia> x = 1.0
```

ist gleichbedeutend mit:

```julia-repl
julia> global x = 1.0
```

Also gelten alle zuvor besprochenen Leistungsprobleme.

## Measure performance with [`@time`](@ref) and pay attention to memory allocation

Ein nützliches Werkzeug zur Messung der Leistung ist das [`@time`](@ref) Makro. Hier wiederholen wir das Beispiel mit der globalen Variablen oben, aber diesmal ohne die Typannotation:

```jldoctest; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_global()
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_global()
  0.011539 seconds (9.08 k allocations: 373.386 KiB, 98.69% compilation time)
523.0007221951678

julia> @time sum_global()
  0.000091 seconds (3.49 k allocations: 70.156 KiB)
523.0007221951678
```

Beim ersten Aufruf (`@time sum_global()`) wird die Funktion kompiliert. (Wenn Sie [`@time`](@ref) in dieser Sitzung noch nicht verwendet haben, werden auch die für das Timing benötigten Funktionen kompiliert.) Sie sollten die Ergebnisse dieses Durchlaufs nicht ernst nehmen. Beim zweiten Durchlauf ist zu beachten, dass zusätzlich zur Zeitberichterstattung auch angezeigt wurde, dass eine erhebliche Menge an Speicher zugewiesen wurde. Wir berechnen hier lediglich eine Summe über alle Elemente in einem Vektor von 64-Bit-Gleitkommazahlen, sodass es keinen Bedarf geben sollte, (Heap-)Speicher zuzuweisen.

Wir sollten klarstellen, dass das, was `@time` berichtet, speziell *Heap*-Allokationen sind, die typischerweise für entweder veränderliche Objekte oder für das Erstellen/Wachsen von variabel großen Containern (wie `Array` oder `Dict`, Strings oder "typ-instabilen" Objekten, deren Typ erst zur Laufzeit bekannt ist) benötigt werden. Das Allokieren (oder Deallokieren) solcher Speicherblöcke kann einen teuren Funktionsaufruf an libc erfordern (z. B. über `malloc` in C), und sie müssen für die Garbage Collection verfolgt werden. Im Gegensatz dazu können unveränderliche Werte wie Zahlen (außer Bignums), Tupel und unveränderliche `struct`s viel günstiger gespeichert werden, z. B. im Stack- oder CPU-Register-Speicher, sodass man sich normalerweise nicht um die Leistungskosten des "Allokierens" dieser Werte kümmern muss.

Unerwartete Speicherzuweisungen sind fast immer ein Zeichen für ein Problem mit Ihrem Code, normalerweise ein Problem mit der Typstabilität oder das Erstellen vieler kleiner temporärer Arrays. Folglich ist es neben der Zuweisung selbst sehr wahrscheinlich, dass der für Ihre Funktion generierte Code weit von optimal entfernt ist. Nehmen Sie solche Hinweise ernst und befolgen Sie die untenstehenden Ratschläge.

In diesem speziellen Fall ist die Speicherzuweisung auf die Verwendung einer typunstabilen globalen Variablen `x` zurückzuführen. Wenn wir stattdessen `x` als Argument an die Funktion übergeben, wird kein Speicher mehr zugewiesen (die verbleibende Zuweisung, die unten gemeldet wird, ist auf die Ausführung des `@time`-Makros im globalen Gültigkeitsbereich zurückzuführen) und ist nach dem ersten Aufruf deutlich schneller:

```jldoctest sumarg; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_arg(x)
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_arg(x)
  0.007551 seconds (3.98 k allocations: 200.548 KiB, 99.77% compilation time)
523.0007221951678

julia> @time sum_arg(x)
  0.000006 seconds (1 allocation: 16 bytes)
523.0007221951678
```

Die 1 Zuweisung, die gesehen wird, stammt von der Ausführung des `@time` Makros selbst im globalen Geltungsbereich. Wenn wir stattdessen das Timing in einer Funktion ausführen, können wir sehen, dass tatsächlich keine Zuweisungen vorgenommen werden:

```jldoctest sumarg; filter = r"[0-9\.]+ seconds"
julia> time_sum(x) = @time sum_arg(x);

julia> time_sum(x)
  0.000002 seconds
523.0007221951678
```

In einigen Situationen muss Ihre Funktion möglicherweise Speicher als Teil ihrer Operation zuweisen, und dies kann das einfache Bild oben komplizieren. In solchen Fällen sollten Sie eine der [tools](@ref tools) unten verwenden, um Probleme zu diagnostizieren, oder eine Version Ihrer Funktion schreiben, die die Zuweisung von ihren algorithmischen Aspekten trennt (siehe [Pre-allocating outputs](@ref)).

!!! note
    Für ernsthafteres Benchmarking sollten Sie das [BenchmarkTools.jl](https://github.com/JuliaCI/BenchmarkTools.jl)-Paket in Betracht ziehen, das unter anderem die Funktion mehrfach auswertet, um Rauschen zu reduzieren.


## [Tools](@id tools)

Julia und sein Paket-Ökosystem umfasst Werkzeuge, die Ihnen helfen können, Probleme zu diagnostizieren und die Leistung Ihres Codes zu verbessern:

  * [Profiling](@ref) ermöglicht es Ihnen, die Leistung Ihres laufenden Codes zu messen und Zeilen zu identifizieren, die als Engpässe dienen. Für komplexe Projekte kann das [ProfileView](https://github.com/timholy/ProfileView.jl)-Paket Ihnen helfen, Ihre Profilierungsergebnisse zu visualisieren.
  * Das [JET](https://github.com/aviatesk/JET.jl) Paket kann Ihnen helfen, häufige Leistungsprobleme in Ihrem Code zu finden.
  * Unerwartet große Speicherzuweisungen – wie berichtet von [`@time`](@ref), [`@allocated`](@ref) oder dem Profiler (durch Aufrufe der Garbage-Collection-Routinen) – deuten darauf hin, dass es Probleme mit Ihrem Code geben könnte. Wenn Sie keinen anderen Grund für die Zuweisungen sehen, vermuten Sie ein Typproblem. Sie können auch Julia mit der Option `--track-allocation=user` starten und die resultierenden `*.mem`-Dateien untersuchen, um Informationen darüber zu erhalten, wo diese Zuweisungen auftreten. Siehe [Memory allocation analysis](@ref).
  * `@code_warntype` erzeugt eine Darstellung Ihres Codes, die hilfreich sein kann, um Ausdrücke zu finden, die zu Typunsicherheit führen. Siehe [`@code_warntype`](@ref) unten.

## [Avoid containers with abstract type parameters](@id man-performance-abstract-container)

Beim Arbeiten mit parametrisierten Typen, einschließlich Arrays, ist es am besten, wo möglich, die Parametrisierung mit abstrakten Typen zu vermeiden.

Bitte den folgenden Text einfügen.

```jldoctest
julia> a = Real[]
Real[]

julia> push!(a, 1); push!(a, 2.0); push!(a, π)
3-element Vector{Real}:
 1
 2.0
 π = 3.1415926535897...
```

Weil `a` ein Array des abstrakten Typs [`Real`](@ref) ist, muss es in der Lage sein, jeden `Real`-Wert zu halten. Da `Real`-Objekte beliebige Größen und Strukturen haben können, muss `a` als ein Array von Zeigern auf individuell zugewiesene `Real`-Objekte dargestellt werden. Wenn wir jedoch stattdessen nur Zahlen desselben Typs, z. B. [`Float64`](@ref), in `a` speichern erlauben, können diese effizienter gespeichert werden:

```jldoctest
julia> a = Float64[]
Float64[]

julia> push!(a, 1); push!(a, 2.0); push!(a,  π)
3-element Vector{Float64}:
 1.0
 2.0
 3.141592653589793
```

Das Zuweisen von Zahlen zu `a` konvertiert sie jetzt in `Float64`, und `a` wird als ein zusammenhängender Block von 64-Bit-Gleitkommawerten gespeichert, die effizient bearbeitet werden können.

Wenn Sie Container mit abstrakten Werttypen nicht vermeiden können, ist es manchmal besser, mit `Any` zu parametrisieren, um die Überprüfung des Typs zur Laufzeit zu vermeiden. Zum Beispiel ist `IdDict{Any, Any}` leistungsfähiger als `IdDict{Type, Vector}`.

Siehe auch die Diskussion unter [Parametric Types](@ref).

## Type declarations

In vielen Sprachen mit optionalen Typdeklarationen ist das Hinzufügen von Deklarationen der Hauptweg, um den Code schneller auszuführen. Das ist *nicht* der Fall in Julia. In Julia kennt der Compiler im Allgemeinen die Typen aller Funktionsargumente, lokalen Variablen und Ausdrücke. Es gibt jedoch einige spezifische Fälle, in denen Deklarationen hilfreich sind.

### Avoid fields with abstract type

Typen können deklariert werden, ohne die Typen ihrer Felder anzugeben:

```jldoctest myambig
julia> struct MyAmbiguousType
           a
       end
```

Dies ermöglicht es, dass `a` von jedem Typ sein kann. Dies kann oft nützlich sein, hat jedoch einen Nachteil: Für Objekte des Typs `MyAmbiguousType` kann der Compiler keinen hochleistungsfähigen Code generieren. Der Grund dafür ist, dass der Compiler die Typen der Objekte und nicht deren Werte verwendet, um zu bestimmen, wie der Code erstellt werden soll. Leider kann über ein Objekt des Typs `MyAmbiguousType` nur sehr wenig abgeleitet werden:

```jldoctest myambig
julia> b = MyAmbiguousType("Hello")
MyAmbiguousType("Hello")

julia> c = MyAmbiguousType(17)
MyAmbiguousType(17)

julia> typeof(b)
MyAmbiguousType

julia> typeof(c)
MyAmbiguousType
```

Die Werte von `b` und `c` haben denselben Typ, dennoch ist ihre zugrunde liegende Datenrepräsentation im Speicher sehr unterschiedlich. Selbst wenn Sie nur numerische Werte im Feld `a` gespeichert haben, bedeutet die Tatsache, dass die Speicherrepräsentation von [`UInt8`](@ref) sich von [`Float64`](@ref) unterscheidet, dass die CPU sie mit zwei verschiedenen Arten von Anweisungen behandeln muss. Da die erforderlichen Informationen im Typ nicht verfügbar sind, müssen solche Entscheidungen zur Laufzeit getroffen werden. Dies verlangsamt die Leistung.

Sie können es besser machen, indem Sie den Typ von `a` deklarieren. Hier konzentrieren wir uns auf den Fall, in dem `a` einer von mehreren Typen sein könnte, in diesem Fall ist die natürliche Lösung, Parameter zu verwenden. Zum Beispiel:

```jldoctest myambig2
julia> mutable struct MyType{T<:AbstractFloat}
           a::T
       end
```

Dies ist eine bessere Wahl als

```jldoctest myambig2
julia> mutable struct MyStillAmbiguousType
           a::AbstractFloat
       end
```

weil die erste Version den Typ von `a` anhand des Typs des Wrapper-Objekts angibt. Zum Beispiel:

```jldoctest myambig2
julia> m = MyType(3.2)
MyType{Float64}(3.2)

julia> t = MyStillAmbiguousType(3.2)
MyStillAmbiguousType(3.2)

julia> typeof(m)
MyType{Float64}

julia> typeof(t)
MyStillAmbiguousType
```

Der Typ des Feldes `a` kann leicht aus dem Typ von `m` bestimmt werden, jedoch nicht aus dem Typ von `t`. Tatsächlich ist es in `t` möglich, den Typ des Feldes `a` zu ändern:

```jldoctest myambig2
julia> typeof(t.a)
Float64

julia> t.a = 4.5f0
4.5f0

julia> typeof(t.a)
Float32
```

Im Gegensatz dazu kann sich der Typ von `m.a` nicht ändern, sobald `m` konstruiert ist:

```jldoctest myambig2
julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float64
```

Die Tatsache, dass der Typ von `m.a` aus dem Typ von `m` bekannt ist – zusammen mit der Tatsache, dass sich sein Typ während der Funktion nicht ändern kann – ermöglicht es dem Compiler, hochoptimierten Code für Objekte wie `m` zu generieren, jedoch nicht für Objekte wie `t`.

Natürlich ist all dies nur wahr, wenn wir `m` mit einem konkreten Typ konstruieren. Wir können dies brechen, indem wir es explizit mit einem abstrakten Typ konstruieren:

```jldoctest myambig2
julia> m = MyType{AbstractFloat}(3.2)
MyType{AbstractFloat}(3.2)

julia> typeof(m.a)
Float64

julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float32
```

Für alle praktischen Zwecke verhalten sich solche Objekte identisch zu denen von `MyStillAmbiguousType`.

Es ist ziemlich lehrreich, die schiere Menge an Code zu vergleichen, die für eine einfache Funktion generiert wird.

```julia
func(m::MyType) = m.a+1
```

benutzen

```julia
code_llvm(func, Tuple{MyType{Float64}})
code_llvm(func, Tuple{MyType{AbstractFloat}})
```

Aus Gründen der Länge werden die Ergebnisse hier nicht angezeigt, aber Sie möchten dies möglicherweise selbst ausprobieren. Da der Typ im ersten Fall vollständig spezifiziert ist, muss der Compiler keinen Code generieren, um den Typ zur Laufzeit aufzulösen. Dies führt zu kürzerem und schnellerem Code.

Man sollte auch im Hinterkopf behalten, dass nicht-vollständig parametrisierte Typen sich wie abstrakte Typen verhalten. Zum Beispiel, obwohl ein vollständig spezifiziertes `Array{T,n}` konkret ist, ist `Array` selbst ohne angegebene Parameter nicht konkret:

```jldoctest myambig3
julia> !isconcretetype(Array), !isabstracttype(Array), isstructtype(Array), !isconcretetype(Array{Int}), isconcretetype(Array{Int,1})
(true, true, true, true, true)
```

In diesem Fall wäre es besser, `MyType` nicht mit einem Feld `a::Array` zu deklarieren, sondern das Feld als `a::Array{T,N}` oder als `a::A` zu deklarieren, wobei `{T,N}` oder `A` Parameter von `MyType` sind.

Der vorherige Rat ist besonders nützlich, wenn die Felder einer Struktur Funktionen oder allgemeiner aufrufbare Objekte sein sollen. Es ist sehr verlockend, eine Struktur wie folgt zu definieren:

```julia
struct MyCallableWrapper
    f::Function
end
```

Aber da `Function` ein abstrakter Typ ist, erfordert jeder Aufruf von `wrapper.f` eine dynamische Dispatch, aufgrund der Typinstabilität beim Zugriff auf das Feld `f`. Stattdessen sollten Sie etwas schreiben wie:

```julia
struct MyCallableWrapper{F}
    f::F
end
```

was nahezu identisches Verhalten aufweist, aber viel schneller sein wird (da die Typinstabilität beseitigt ist). Beachten Sie, dass wir `F<:Function` nicht auferlegen: Das bedeutet, dass auch aufrufbare Objekte, die nicht von `Function` abgeleitet sind, für das Feld `f` erlaubt sind.

### Avoid fields with abstract containers

Die gleichen Best Practices gelten auch für Containertypen:

```jldoctest containers
julia> struct MySimpleContainer{A<:AbstractVector}
           a::A
       end

julia> struct MyAmbiguousContainer{T}
           a::AbstractVector{T}
       end

julia> struct MyAlsoAmbiguousContainer
           a::Array
       end
```

Zum Beispiel:

```jldoctest containers
julia> c = MySimpleContainer(1:3);

julia> typeof(c)
MySimpleContainer{UnitRange{Int64}}

julia> c = MySimpleContainer([1:3;]);

julia> typeof(c)
MySimpleContainer{Vector{Int64}}

julia> b = MyAmbiguousContainer(1:3);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> b = MyAmbiguousContainer([1:3;]);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> d = MyAlsoAmbiguousContainer(1:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Int64})

julia> d = MyAlsoAmbiguousContainer(1:1.0:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Float64})

```

Für `MySimpleContainer` ist das Objekt vollständig durch seinen Typ und seine Parameter spezifiziert, sodass der Compiler optimierte Funktionen generieren kann. In den meisten Fällen wird dies wahrscheinlich ausreichen.

Während der Compiler jetzt seine Aufgabe perfekt erfüllen kann, gibt es Fälle, in denen *du* dir wünschen könntest, dass dein Code je nach *Elementtyp* von `a` unterschiedliche Dinge tun könnte. In der Regel ist der beste Weg, dies zu erreichen, deine spezifische Operation (hier `foo`) in eine separate Funktion zu kapseln:

```jldoctest containers
julia> function sumfoo(c::MySimpleContainer)
           s = 0
           for x in c.a
               s += foo(x)
           end
           s
       end
sumfoo (generic function with 1 method)

julia> foo(x::Integer) = x
foo (generic function with 1 method)

julia> foo(x::AbstractFloat) = round(x)
foo (generic function with 2 methods)
```

Dies hält die Dinge einfach, während der Compiler in allen Fällen optimierten Code generieren kann.

Es gibt jedoch Fälle, in denen Sie möglicherweise verschiedene Versionen der äußeren Funktion für unterschiedliche Elementtypen oder Typen des `AbstractVector` des Feldes `a` in `MySimpleContainer` deklarieren müssen. Sie könnten es so machen:

```jldoctest containers
julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:Integer}})
           return c.a[1]+1
       end
myfunc (generic function with 1 method)

julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:AbstractFloat}})
           return c.a[1]+2
       end
myfunc (generic function with 2 methods)

julia> function myfunc(c::MySimpleContainer{Vector{T}}) where T <: Integer
           return c.a[1]+3
       end
myfunc (generic function with 3 methods)
```

```jldoctest containers
julia> myfunc(MySimpleContainer(1:3))
2

julia> myfunc(MySimpleContainer(1.0:3))
3.0

julia> myfunc(MySimpleContainer([1:3;]))
4
```

### Annotate values taken from untyped locations

Es ist oft praktisch, mit Datenstrukturen zu arbeiten, die Werte beliebigen Typs enthalten können (Arrays vom Typ `Array{Any}`). Aber wenn Sie eine dieser Strukturen verwenden und zufällig den Typ eines Elements kennen, hilft es, dieses Wissen mit dem Compiler zu teilen:

```julia
function foo(a::Array{Any,1})
    x = a[1]::Int32
    b = x+1
    ...
end
```

Hier wussten wir zufällig, dass das erste Element von `a` ein [`Int32`](@ref) sein würde. Eine Annotation wie diese hat den zusätzlichen Vorteil, dass sie einen Laufzeitfehler auslöst, wenn der Wert nicht vom erwarteten Typ ist, was potenziell bestimmte Fehler früher aufdecken kann.

Im Falle, dass der Typ von `a[1]` nicht genau bekannt ist, kann `x` über `x = convert(Int32, a[1])::Int32` deklariert werden. Die Verwendung der [`convert`](@ref)-Funktion ermöglicht es, dass `a[1]` jedes Objekt sein kann, das in ein `Int32` konvertierbar ist (wie z.B. `UInt8`), wodurch die Allgemeingültigkeit des Codes erhöht wird, indem die Typanforderung gelockert wird. Beachten Sie, dass `convert` in diesem Kontext selbst eine Typannotation benötigt, um Typstabilität zu erreichen. Dies liegt daran, dass der Compiler den Typ des Rückgabewerts einer Funktion, selbst `convert`, nicht ableiten kann, es sei denn, die Typen aller Argumente der Funktion sind bekannt.

Typannotationen verbessern (und können tatsächlich die Leistung beeinträchtigen), wenn der Typ abstrakt oder zur Laufzeit erstellt wird. Dies liegt daran, dass der Compiler die Annotation nicht verwenden kann, um den nachfolgenden Code zu spezialisieren, und die Typüberprüfung selbst Zeit in Anspruch nimmt. Zum Beispiel im Code:

```julia
function nr(a, prec)
    ctype = prec == 32 ? Float32 : Float64
    b = Complex{ctype}(a)
    c = (b + 1.0f0)::Complex{ctype}
    abs(c)
end
```

die Annotation von `c` schadet der Leistung. Um leistungsfähigen Code zu schreiben, der zur Laufzeit konstruierte Typen verwendet, nutzen Sie die [function-barrier technique](@ref kernel-functions), die unten besprochen wird, und stellen Sie sicher, dass der konstruierte Typ unter den Argumenttypen der Kernel-Funktion erscheint, damit die Kernel-Operationen vom Compiler ordnungsgemäß spezialisiert werden. Zum Beispiel kann `b`, sobald es konstruiert ist, an eine andere Funktion `k`, den Kernel, übergeben werden. Wenn die Funktion `k` beispielsweise `b` als Argument vom Typ `Complex{T}` deklariert, wobei `T` ein Typparameter ist, dann erscheint eine Typannotation in einer Zuweisungsanweisung innerhalb von `k` in der Form:

```julia
c = (b + 1.0f0)::Complex{T}
```

beeinträchtigt die Leistung nicht (hilft aber auch nicht), da der Compiler den Typ von `c` zum Zeitpunkt der Kompilierung von `k` bestimmen kann.

### Be aware of when Julia avoids specializing

Als Heuristik vermeidet Julia automatisch [specializing](@ref man-method-specializations) bei Argumenttyp-Parametern in drei spezifischen Fällen: `Type`, `Function` und `Vararg`. Julia wird immer spezialisieren, wenn das Argument innerhalb der Methode verwendet wird, jedoch nicht, wenn das Argument nur an eine andere Funktion weitergegeben wird. Dies hat normalerweise keine Leistungsbeeinträchtigung zur Laufzeit und [improves compiler performance](@ref compiler-efficiency-issues). Wenn Sie feststellen, dass es in Ihrem Fall eine Leistungsbeeinträchtigung zur Laufzeit hat, können Sie die Spezialisierung auslösen, indem Sie einen Typ-Parameter zur Methodendeklaration hinzufügen. Hier sind einige Beispiele:

Das wird nicht spezialisiert:

```julia
function f_type(t)  # or t::Type
    x = ones(t, 10)
    return sum(map(sin, x))
end
```

aber das wird:

```julia
function g_type(t::Type{T}) where T
    x = ones(T, 10)
    return sum(map(sin, x))
end
```

Diese werden sich nicht spezialisieren:

```julia
f_func(f, num) = ntuple(f, div(num, 2))
g_func(g::Function, num) = ntuple(g, div(num, 2))
```

aber das wird:

```julia
h_func(h::H, num) where {H} = ntuple(h, div(num, 2))
```

Das wird nicht spezialisiert:

```julia
f_vararg(x::Int...) = tuple(x...)
```

aber das wird:

```julia
g_vararg(x::Vararg{Int, N}) where {N} = tuple(x...)
```

Man muss nur einen einzigen Typ-Parameter einführen, um eine Spezialisierung zu erzwingen, selbst wenn die anderen Typen nicht eingeschränkt sind. Zum Beispiel wird dies auch spezialisieren und ist nützlich, wenn die Argumente nicht alle vom gleichen Typ sind:

```julia
h_vararg(x::Vararg{Any, N}) where {N} = tuple(x...)
```

Beachten Sie, dass [`@code_typed`](@ref) und Freunde Ihnen immer spezialisierten Code anzeigen, selbst wenn Julia diesen Methodenaufruf normalerweise nicht spezialisieren würde. Sie müssen [method internals](@ref ast-lowered-method) überprüfen, wenn Sie sehen möchten, ob Spezialisierungen generiert werden, wenn sich die Argumenttypen ändern, d.h. ob `Base.specializations(@which f(...))` Spezialisierungen für das betreffende Argument enthält.

## Break functions into multiple definitions

Das Schreiben einer Funktion als viele kleine Definitionen ermöglicht es dem Compiler, den am besten geeigneten Code direkt aufzurufen oder ihn sogar inline zu setzen.

Hier ist ein Beispiel für eine "Zusammengesetzte Funktion", die wirklich als mehrere Definitionen geschrieben werden sollte:

```julia
using LinearAlgebra

function mynorm(A)
    if isa(A, Vector)
        return sqrt(real(dot(A,A)))
    elseif isa(A, Matrix)
        return maximum(svdvals(A))
    else
        error("mynorm: invalid argument")
    end
end
```

Dies kann präziser und effizienter formuliert werden als:

```julia
mynorm(x::Vector) = sqrt(real(dot(x, x)))
mynorm(A::Matrix) = maximum(svdvals(A))
```

Es sollte jedoch beachtet werden, dass der Compiler ziemlich effizient darin ist, die toten Zweige im Code, der wie das `mynorm`-Beispiel geschrieben ist, zu optimieren.

## Write "type-stable" functions

Wenn möglich, hilft es sicherzustellen, dass eine Funktion immer einen Wert des gleichen Typs zurückgibt. Betrachten Sie die folgende Definition:

```julia
pos(x) = x < 0 ? 0 : x
```

Obwohl dies harmlos genug erscheint, besteht das Problem darin, dass `0` eine Ganzzahl (vom Typ `Int`) ist und `x` von jedem Typ sein könnte. Je nach Wert von `x` könnte diese Funktion also einen Wert eines von zwei Typen zurückgeben. Dieses Verhalten ist zulässig und kann in einigen Fällen wünschenswert sein. Aber es kann leicht wie folgt behoben werden:

```julia
pos(x) = x < 0 ? zero(x) : x
```

Es gibt auch eine [`oneunit`](@ref)-Funktion und eine allgemeinere [`oftype(x, y)`](@ref)-Funktion, die `y` in den Typ von `x` umwandelt.

## Avoid changing the type of a variable

Ein analoges Problem der "Typ-Stabilität" besteht für Variablen, die innerhalb einer Funktion wiederholt verwendet werden:

```julia
function foo()
    x = 1
    for i = 1:10
        x /= rand()
    end
    return x
end
```

Lokale Variable `x` beginnt als Ganzzahl und wird nach einer Schleifeniteration zu einer Fließkommazahl (das Ergebnis des [`/`](@ref) Operators). Dies erschwert es dem Compiler, den Körper der Schleife zu optimieren. Es gibt mehrere mögliche Lösungen:

  * Initialisiere `x` mit `x = 1.0`
  * Deklariere den Typ von `x` explizit als `x::Float64 = 1`
  * Verwenden Sie eine explizite Konvertierung durch `x = oneunit(Float64)`
  * Initialisieren Sie mit der ersten Schleifeniteration, um `x = 1 / rand()` zu setzen, dann Schleife `for i = 2:10`

## [Separate kernel functions (aka, function barriers)](@id kernel-functions)

Viele Funktionen folgen einem Muster, bei dem zunächst einige Vorbereitungsarbeiten durchgeführt werden und dann viele Iterationen ablaufen, um eine Kernberechnung durchzuführen. Wo immer möglich, ist es eine gute Idee, diese Kernberechnungen in separate Funktionen zu packen. Zum Beispiel gibt die folgende erfundene Funktion ein Array eines zufällig gewählten Typs zurück:

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           for i = 1:n
               a[i] = 2
           end
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

Das sollte so geschrieben werden:

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function fill_twos!(a)
           for i = eachindex(a)
               a[i] = 2
           end
       end;

julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           fill_twos!(a)
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

Julias Compiler spezialisiert Code für Argumenttypen an Funktionsgrenzen, sodass er in der ursprünglichen Implementierung den Typ von `a` während der Schleife nicht kennt (da er zufällig gewählt wird). Daher ist die zweite Version im Allgemeinen schneller, da die innere Schleife als Teil von `fill_twos!` für verschiedene Typen von `a` neu kompiliert werden kann.

Die zweite Form ist auch oft der bessere Stil und kann zu mehr Code-Wiederverwendung führen.

Dieses Muster wird an mehreren Stellen in Julia Base verwendet. Zum Beispiel siehe `vcat` und `hcat` in [`abstractarray.jl`](https://github.com/JuliaLang/julia/blob/40fe264f4ffaa29b749bcf42239a89abdcbba846/base/abstractarray.jl#L1205-L1206), oder die [`fill!`](@ref) Funktion, die wir anstelle von `fill_twos!` hätten verwenden können.

Funktionen wie `strange_twos` treten auf, wenn man mit Daten unsicherer Typen umgeht, zum Beispiel mit Daten, die aus einer Eingabedatei geladen wurden, die entweder Ganzzahlen, Fließkommazahlen, Zeichenfolgen oder etwas anderes enthalten könnte.

## [Types with values-as-parameters](@id man-performance-value-type)

Angenommen, Sie möchten ein `N`-dimensionales Array erstellen, das entlang jeder Achse die Größe 3 hat. Solche Arrays können wie folgt erstellt werden:

```jldoctest
julia> A = fill(5.0, (3, 3))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Dieser Ansatz funktioniert sehr gut: Der Compiler kann herausfinden, dass `A` ein `Array{Float64,2}` ist, da er den Typ des Füllwerts (`5.0::Float64`) und die Dimensionalität (`(3, 3)::NTuple{2,Int}`) kennt. Das bedeutet, dass der Compiler sehr effizienten Code für jede zukünftige Verwendung von `A` in derselben Funktion generieren kann.

Aber jetzt nehmen wir an, Sie möchten eine Funktion schreiben, die ein 3×3×... Array in beliebigen Dimensionen erstellt; Sie könnten versucht sein, eine Funktion zu schreiben

```jldoctest
julia> function array3(fillval, N)
           fill(fillval, ntuple(d->3, N))
       end
array3 (generic function with 1 method)

julia> array3(5.0, 2)
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Das funktioniert, aber (wie Sie selbst mit `@code_warntype array3(5.0, 2)` überprüfen können) besteht das Problem darin, dass der Ausgabetyp nicht abgeleitet werden kann: Das Argument `N` ist ein *Wert* vom Typ `Int`, und die Typableitung kann dessen Wert im Voraus nicht vorhersagen. Das bedeutet, dass Code, der die Ausgabe dieser Funktion verwendet, vorsichtig sein muss und den Typ bei jedem Zugriff auf `A` überprüfen muss; solcher Code wird sehr langsam sein.

Jetzt ist eine sehr gute Möglichkeit, solche Probleme zu lösen, die Verwendung von [function-barrier technique](@ref kernel-functions). In einigen Fällen möchten Sie jedoch die Typinstabilität ganz beseitigen. In solchen Fällen ist ein Ansatz, die Dimensionalität als Parameter zu übergeben, zum Beispiel durch `Val{T}()` (siehe ["Value types"](@ref)):

```jldoctest
julia> function array3(fillval, ::Val{N}) where N
           fill(fillval, ntuple(d->3, Val(N)))
       end
array3 (generic function with 1 method)

julia> array3(5.0, Val(2))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Julia hat eine spezialisierte Version von `ntuple`, die eine `Val{::Int}`-Instanz als zweiten Parameter akzeptiert; indem Sie `N` als Typ-Parameter übergeben, machen Sie dessen "Wert" dem Compiler bekannt. Folglich ermöglicht diese Version von `array3` dem Compiler, den Rückgabetyp vorherzusagen.

Es kann jedoch überraschend subtil sein, solche Techniken zu verwenden. Zum Beispiel wäre es nicht hilfreich, wenn Sie `array3` aus einer Funktion wie dieser aufrufen:

```julia
function call_array3(fillval, n)
    A = array3(fillval, Val(n))
end
```

Hier haben Sie das gleiche Problem erneut geschaffen: Der Compiler kann nicht erraten, was `n` ist, daher kennt er den *Typ* von `Val(n)`. Der Versuch, `Val` zu verwenden, aber dies falsch zu tun, kann in vielen Situationen die Leistung *verschlechtern*. (Nur in Situationen, in denen Sie `Val` effektiv mit dem Funktionsbarrieretrick kombinieren, um die Kernel-Funktion effizienter zu gestalten, sollte Code wie der oben verwendete eingesetzt werden.)

Ein Beispiel für die korrekte Verwendung von `Val` wäre:

```julia
function filter3(A::AbstractArray{T,N}) where {T,N}
    kernel = array3(1, Val(N))
    filter(A, kernel)
end
```

In diesem Beispiel wird `N` als Parameter übergeben, sodass sein "Wert" dem Compiler bekannt ist. Im Wesentlichen funktioniert `Val(T)` nur, wenn `T` entweder fest codiert/literal (`Val(3)`) oder bereits im Typbereich angegeben ist.

## The dangers of abusing multiple dispatch (aka, more on types with values-as-parameters)

Sobald man lernt, multiple Dispatch zu schätzen, gibt es eine verständliche Tendenz, über das Ziel hinauszuschießen und zu versuchen, es für alles zu verwenden. Zum Beispiel könnte man sich vorstellen, es zu verwenden, um Informationen zu speichern, z.B.

```
struct Car{Make, Model}
    year::Int
    ...more fields...
end
```

und dann auf Objekte wie `Car{:Honda,:Accord}(Jahr, args...)` dispatchen.

Dies könnte lohnenswert sein, wenn einer der folgenden Punkte zutrifft:

  * Sie benötigen CPU-intensive Verarbeitung für jedes `Auto`, und es wird erheblich effizienter, wenn Sie die `Marke` und das `Modell` zur Compile-Zeit kennen und die Gesamtzahl der verschiedenen `Marken` oder `Modelle`, die verwendet werden, nicht zu groß ist.
  * Sie haben homogene Listen desselben Typs `Car` zu verarbeiten, sodass Sie sie alle in einem `Array{Car{:Honda,:Accord},N}` speichern können.

Wenn Letzteres zutrifft, kann eine Funktion, die ein solches homogenes Array verarbeitet, produktiv spezialisiert werden: Julia kennt den Typ jedes Elements im Voraus (alle Objekte im Container haben denselben konkreten Typ), sodass Julia die richtigen Methodenaufrufe beim Kompilieren der Funktion "nachschlagen" kann (was die Notwendigkeit einer Überprüfung zur Laufzeit überflüssig macht) und somit effizienten Code zur Verarbeitung der gesamten Liste erzeugen kann.

Wenn diese Bedingungen nicht erfüllt sind, ist es wahrscheinlich, dass Sie keinen Nutzen daraus ziehen; schlimmer noch, die resultierende "kombinatorische Explosion der Typen" wird kontraproduktiv sein. Wenn `items[i+1]` einen anderen Typ hat als `item[i]`, muss Julia den Typ zur Laufzeit nachschlagen, nach der entsprechenden Methode in den Methodentabellen suchen, entscheiden (über die Typ-Intersection), welche übereinstimmt, feststellen, ob sie bereits JIT-compiliert wurde (und dies tun, falls nicht), und dann den Aufruf tätigen. Im Wesentlichen fordern Sie das gesamte Typsystem und die JIT-Kompilierungsmechanismen auf, im Grunde das Äquivalent einer Switch-Anweisung oder eines Wörterbuch-Lookups in Ihrem eigenen Code auszuführen.

Einige Laufzeit-Benchmarks, die (1) Typdispatch, (2) Wörterbuchsuche und (3) eine "Switch"-Anweisung vergleichen, sind zu finden [on the mailing list](https://groups.google.com/forum/#!msg/julia-users/jUMu9A3QKQQ/qjgVWr7vAwAJ).

Vielleicht ist der Compile-Zeit-Einfluss sogar schlimmer als der Laufzeit-Einfluss: Julia wird spezialisierte Funktionen für jeden unterschiedlichen `Car{Make, Model}` kompilieren; wenn Sie Hunderte oder Tausende solcher Typen haben, dann wird jede Funktion, die ein solches Objekt als Parameter akzeptiert (von einer benutzerdefinierten `get_year`-Funktion, die Sie selbst schreiben könnten, bis zur generischen `push!`-Funktion in Julia Base), Hunderte oder Tausende von Varianten dafür kompiliert haben. Jede dieser Varianten erhöht die Größe des Caches für kompilierte Codes, die Länge interner Listen von Methoden usw. Übermäßiger Enthusiasmus für Werte als Parameter kann leicht enorme Ressourcen verschwenden.

## [Access arrays in memory order, along columns](@id man-performance-column-major)

Mehrdimensionale Arrays in Julia werden in Spalten-Hauptreihenfolge gespeichert. Das bedeutet, dass Arrays spaltenweise gestapelt werden. Dies kann mit der Funktion `vec` oder der Syntax `[:]` überprüft werden, wie unten gezeigt (beachten Sie, dass das Array in der Reihenfolge `[1 3 2 4]` und nicht `[1 2 3 4]` angeordnet ist):

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> x[:]
4-element Vector{Int64}:
 1
 3
 2
 4
```

Diese Konvention zur Anordnung von Arrays ist in vielen Sprachen wie Fortran, Matlab und R (um nur einige zu nennen) verbreitet. Die Alternative zur spaltenbasierten Anordnung ist die zeilenbasierte Anordnung, die von C und Python (`numpy`) sowie anderen Sprachen übernommen wird. Sich an die Anordnung von Arrays zu erinnern, kann erhebliche Leistungseffekte beim Durchlaufen von Arrays haben. Eine Faustregel, die man im Hinterkopf behalten sollte, ist, dass bei spaltenbasierten Arrays der erste Index am schnellsten wechselt. Im Wesentlichen bedeutet dies, dass das Durchlaufen schneller ist, wenn der innerste Schleifenindex der erste ist, der in einem Slice-Ausdruck erscheint. Beachten Sie, dass das Indizieren eines Arrays mit `:` eine implizite Schleife ist, die iterativ auf alle Elemente innerhalb einer bestimmten Dimension zugreift; es kann schneller sein, Spalten als Zeilen zu extrahieren, zum Beispiel.

Betrachten Sie das folgende konstruierte Beispiel. Stellen Sie sich vor, wir wollten eine Funktion schreiben, die einen [`Vector`](@ref) akzeptiert und ein Quadrat [`Matrix`](@ref) zurückgibt, wobei entweder die Zeilen oder die Spalten mit Kopien des Eingangsvektors gefüllt sind. Angenommen, es ist nicht wichtig, ob die Zeilen oder Spalten mit diesen Kopien gefüllt sind (vielleicht kann der Rest des Codes entsprechend leicht angepasst werden). Wir könnten dies auf mindestens vier Arten tun (neben dem empfohlenen Aufruf der integrierten [`repeat`](@ref)):

```julia
function copy_cols(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[:, i] = x
    end
    return out
end

function copy_rows(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[i, :] = x
    end
    return out
end

function copy_col_row(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for col = inds, row = inds
        out[row, col] = x[row]
    end
    return out
end

function copy_row_col(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for row = inds, col = inds
        out[row, col] = x[col]
    end
    return out
end
```

Jetzt werden wir jede dieser Funktionen mit demselben zufälligen `10000` mal `1` Eingangsvektor zeitlich messen:

```julia-repl
julia> x = randn(10000);

julia> fmt(f) = println(rpad(string(f)*": ", 14, ' '), @elapsed f(x))

julia> map(fmt, [copy_cols, copy_rows, copy_col_row, copy_row_col]);
copy_cols:    0.331706323
copy_rows:    1.799009911
copy_col_row: 0.415630047
copy_row_col: 1.721531501
```

Beachten Sie, dass `copy_cols` viel schneller ist als `copy_rows`. Das ist zu erwarten, da `copy_cols` das spaltenbasierte Speicherlayout der `Matrix` respektiert und es eine Spalte nach der anderen ausfüllt. Darüber hinaus ist `copy_col_row` viel schneller als `copy_row_col`, da es unserer Faustregel folgt, dass das erste Element, das in einem Slice-Ausdruck erscheint, mit der innersten Schleife gekoppelt werden sollte.

## Pre-allocating outputs

Wenn Ihre Funktion ein `Array` oder einen anderen komplexen Typ zurückgibt, muss möglicherweise Speicher zugewiesen werden. Leider sind die Speicherzuweisung und deren Gegenteil, die Müllabfuhr, oft erhebliche Engpässe.

Manchmal können Sie die Notwendigkeit umgehen, bei jedem Funktionsaufruf Speicher zuzuweisen, indem Sie die Ausgabe vorab zuweisen. Als triviales Beispiel vergleichen Sie

```jldoctest prealloc
julia> function xinc(x)
           return [x, x+1, x+2]
       end;

julia> function loopinc()
           y = 0
           for i = 1:10^7
               ret = xinc(i)
               y += ret[2]
           end
           return y
       end;
```

mit

```jldoctest prealloc
julia> function xinc!(ret::AbstractVector{T}, x::T) where T
           ret[1] = x
           ret[2] = x+1
           ret[3] = x+2
           nothing
       end;

julia> function loopinc_prealloc()
           ret = Vector{Int}(undef, 3)
           y = 0
           for i = 1:10^7
               xinc!(ret, i)
               y += ret[2]
           end
           return y
       end;
```

Timing-Ergebnisse:

```jldoctest prealloc; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> @time loopinc()
  0.529894 seconds (40.00 M allocations: 1.490 GiB, 12.14% gc time)
50000015000000

julia> @time loopinc_prealloc()
  0.030850 seconds (6 allocations: 288 bytes)
50000015000000
```

Die Vorabzuweisung hat weitere Vorteile, zum Beispiel, indem sie dem Aufrufer ermöglicht, den "Ausgabe"-Typ eines Algorithmus zu steuern. Im obigen Beispiel hätten wir anstelle von [`Array`](@ref) auch ein `SubArray` übergeben können, wenn wir das gewünscht hätten.

Bis zu einem gewissen Grad kann die Vorabzuweisung Ihren Code unansehnlich machen, sodass Leistungsmessungen und etwas Urteilsvermögen erforderlich sein können. Für "vektorisierte" (elementweise) Funktionen kann jedoch die bequeme Syntax `x .= f.(y)` für In-Place-Operationen mit fusionierten Schleifen und ohne temporäre Arrays verwendet werden (siehe die [dot syntax for vectorizing functions](@ref man-vectorized)).

## [Use `MutableArithmetics` for more control over allocation for mutable arithmetic types](@id man-perftips-mutablearithmetics)

Einige [`Number`](@ref) Subtypen, wie [`BigInt`](@ref) oder [`BigFloat`](@ref), können als [`mutable struct`](@ref) Typen implementiert werden oder sie können veränderbare Komponenten haben. Die arithmetischen Schnittstellen in Julia `Base` entscheiden sich in solchen Fällen normalerweise für Bequemlichkeit über Effizienz, sodass die Verwendung in naiver Weise zu suboptimaler Leistung führen kann. Die Abstraktionen des [`MutableArithmetics`](https://juliahub.com/ui/Packages/General/MutableArithmetics) Pakets hingegen ermöglichen es, die Veränderlichkeit solcher Typen auszunutzen, um schnellen Code zu schreiben, der nur so viel allokiert, wie notwendig ist. `MutableArithmetics` ermöglicht es auch, Werte von veränderbaren arithmetischen Typen bei Bedarf explizit zu kopieren. `MutableArithmetics` ist ein Benutzerpaket und ist nicht mit dem Julia-Projekt verbunden.

## More dots: Fuse vectorized operations

Julia hat eine spezielle [dot syntax](@ref man-vectorized), die jede skalare Funktion in einen "vektorisierten" Funktionsaufruf und jeden Operator in einen "vektorisierten" Operator umwandelt, mit der besonderen Eigenschaft, dass geschachtelte "Punktaufrufe" *fusionieren*: sie werden auf der Syntaxebene in eine einzige Schleife kombiniert, ohne temporäre Arrays zuzuweisen. Wenn Sie `.=` und ähnliche Zuweisungsoperatoren verwenden, kann das Ergebnis auch in einem vorab zugewiesenen Array in-place gespeichert werden (siehe oben).

In einem linearen Algebra-Kontext bedeutet dies, dass, obwohl Operationen wie `vector + vector` und `vector * scalar` definiert sind, es vorteilhaft sein kann, stattdessen `vector .+ vector` und `vector .* scalar` zu verwenden, da die resultierenden Schleifen mit umgebenden Berechnungen fusioniert werden können. Betrachten Sie zum Beispiel die beiden Funktionen:

```jldoctest dotfuse
julia> f(x) = 3x.^2 + 4x + 7x.^3;

julia> fdot(x) = @. 3x^2 + 4x + 7x^3; # equivalent to 3 .* x.^2 .+ 4 .* x .+ 7 .* x.^3
```

Sowohl `f` als auch `fdot` berechnen dasselbe. Allerdings ist `fdot` (definiert mit Hilfe des [`@.`](@ref @__dot__) Makros) erheblich schneller, wenn es auf ein Array angewendet wird:

```jldoctest dotfuse; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(10^6);

julia> @time f(x);
  0.019049 seconds (16 allocations: 45.777 MiB, 18.59% gc time)

julia> @time fdot(x);
  0.002790 seconds (6 allocations: 7.630 MiB)

julia> @time f.(x);
  0.002626 seconds (8 allocations: 7.630 MiB)
```

Das heißt, `fdot(x)` ist zehnmal schneller und benötigt 1/6 des Speichers von `f(x)`, da jede `*`- und `+`-Operation in `f(x)` ein neues temporäres Array allokiert und in einer separaten Schleife ausgeführt wird. In diesem Beispiel ist `f.(x)` so schnell wie `fdot(x)`, aber in vielen Kontexten ist es praktischer, einige Punkte in Ihren Ausdrücken zu streuen, als für jede vektorisierte Operation eine separate Funktion zu definieren.

## [Fewer dots: Unfuse certain intermediate broadcasts](@id man-performance-unfuse)

Die oben erwähnte Punkt-Schleifenfusion ermöglicht einen prägnanten und idiomatischen Code, um hochleistungsfähige Operationen auszudrücken. Es ist jedoch wichtig, sich daran zu erinnern, dass die fusionierte Operation bei jeder Iteration des Broadcasts berechnet wird. Das bedeutet, dass in einigen Situationen, insbesondere in Anwesenheit von zusammengesetzten oder mehrdimensionalen Broadcasts, ein Ausdruck mit Punktaufrufen eine Funktion möglicherweise häufiger berechnet, als beabsichtigt. Zum Beispiel, sagen wir, wir möchten eine Zufallsmatrix erstellen, deren Zeilen die euklidische Norm eins haben. Wir könnten etwas wie Folgendes schreiben:

```
julia> x = rand(1000, 1000);

julia> d = sum(abs2, x; dims=2);

julia> @time x ./= sqrt.(d);
  0.002049 seconds (4 allocations: 96 bytes)
```

Das wird funktionieren. Diese Ausdruck wird jedoch tatsächlich `sqrt(d[i])` für *jedes* Element in der Zeile `x[i, :]` neu berechnen, was bedeutet, dass viel mehr Quadratwurzeln berechnet werden, als notwendig. Um genau zu sehen, über welche Indizes die Übertragung iterieren wird, können wir `Broadcast.combine_axes` auf die Argumente des zusammengefassten Ausdrucks aufrufen. Dies wird ein Tupel von Bereichen zurückgeben, deren Einträge den Iterationsachsen entsprechen; das Produkt der Längen dieser Bereiche wird die Gesamtzahl der Aufrufe der zusammengefassten Operation sein.

Es folgt, dass wenn einige Komponenten des Broadcast-Ausdrucks entlang einer Achse konstant sind—wie das `sqrt` entlang der zweiten Dimension im vorhergehenden Beispiel—das Potenzial für eine Leistungsverbesserung besteht, indem man diese Komponenten gewaltsam "entfused", d.h. das Ergebnis der broadcasteten Operation im Voraus zuzuweisen und den zwischengespeicherten Wert entlang seiner konstanten Achse wiederzuverwenden. Einige solcher potenziellen Ansätze sind die Verwendung von temporären Variablen, das Einwickeln von Komponenten eines Punktausdrucks in `identity` oder die Verwendung einer äquivalenten intrinsisch vektorisierte (aber nicht fusionierte) Funktion.

```
julia> @time let s = sqrt.(d); x ./= s end;
  0.000809 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= identity(sqrt.(d));
  0.000608 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= map(sqrt, d);
  0.000611 seconds (4 allocations: 8.016 KiB)
```

Jede dieser Optionen führt zu einer ungefähr dreifachen Beschleunigung auf Kosten einer Zuweisung; bei großen Broadcastables kann diese Beschleunigung asymptotisch sehr groß sein.

## [Consider using views for slices](@id man-performance-views)

In Julia erstellt ein Array "Slice"-Ausdruck wie `array[1:5, :]` eine Kopie dieser Daten (außer auf der linken Seite einer Zuweisung, wo `array[1:5, :] = ...` in-place in diesen Teil von `array` zuweist). Wenn Sie viele Operationen auf dem Slice durchführen, kann dies gut für die Leistung sein, da es effizienter ist, mit einer kleineren zusammenhängenden Kopie zu arbeiten, als in das ursprüngliche Array zu indizieren. Andererseits, wenn Sie nur ein paar einfache Operationen auf dem Slice durchführen, können die Kosten für die Zuweisung und Kopieroperationen erheblich sein.

Eine Alternative besteht darin, eine "Ansicht" des Arrays zu erstellen, die ein Array-Objekt (ein `SubArray`) ist, das tatsächlich die Daten des ursprünglichen Arrays vor Ort referenziert, ohne eine Kopie zu erstellen. (Wenn Sie in eine Ansicht schreiben, wird auch die Daten des ursprünglichen Arrays geändert.) Dies kann für einzelne Schnitte erfolgen, indem Sie [`view`](@ref) aufrufen, oder einfacher für einen ganzen Ausdruck oder Block von Code, indem Sie [`@views`](@ref) vor diesen Ausdruck setzen. Zum Beispiel:

```jldoctest; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> fcopy(x) = sum(x[2:end-1]);

julia> @views fview(x) = sum(x[2:end-1]);

julia> x = rand(10^6);

julia> @time fcopy(x);
  0.003051 seconds (3 allocations: 7.629 MB)

julia> @time fview(x);
  0.001020 seconds (1 allocation: 16 bytes)
```

Beachten Sie sowohl die 3× Beschleunigung als auch die verringerte Speicherzuweisung der `fview`-Version der Funktion.

## Copying data is not always bad

Arrays werden zusammenhängend im Speicher gespeichert, was sie für die CPU-Vektorisierung und weniger Speicherzugriffe aufgrund von Caching geeignet macht. Dies sind die gleichen Gründe, aus denen empfohlen wird, Arrays in spaltenmajorer Reihenfolge zuzugreifen (siehe oben). Unregelmäßige Zugriffsarten und nicht zusammenhängende Ansichten können Berechnungen auf Arrays drastisch verlangsamen, da der Speicher nicht sequenziell zugegriffen wird.

Das Kopieren von unregelmäßig zugegriffenem Daten in ein zusammenhängendes Array, bevor es wiederholt zugegriffen wird, kann zu einer erheblichen Geschwindigkeitssteigerung führen, wie im folgenden Beispiel. Hier wird eine Matrix an zufällig gemischten Indizes zugegriffen, bevor sie multipliziert wird. Das Kopieren in einfache Arrays beschleunigt die Multiplikation, selbst mit den zusätzlichen Kosten für das Kopieren und die Zuweisung.

```julia-repl
julia> using Random

julia> A = randn(3000, 3000);

julia> x = randn(2000);

julia> inds = shuffle(1:3000)[1:2000];

julia> function iterated_neural_network(A, x, depth)
           for _ in 1:depth
               x .= max.(0, A * x)
           end
           argmax(x)
       end

julia> @time iterated_neural_network(view(A, inds, inds), x, 10)
  0.324903 seconds (12 allocations: 157.562 KiB)
1569

julia> @time iterated_neural_network(A[inds, inds], x, 10)
  0.054576 seconds (13 allocations: 30.671 MiB, 13.33% gc time)
1569
```

Vorausgesetzt, es ist genügend Speicher vorhanden, überwiegt die Kosten für das Kopieren der Ansicht in ein Array den Geschwindigkeitsvorteil, der sich aus den wiederholten Matrixmultiplikationen auf einem zusammenhängenden Array ergibt.

## Consider StaticArrays.jl for small fixed-size vector/matrix operations

Wenn Ihre Anwendung viele kleine (`< 100` Elemente) Arrays fester Größen (d.h. die Größe ist vor der Ausführung bekannt) umfasst, sollten Sie in Betracht ziehen, das [StaticArrays.jl package](https://github.com/JuliaArrays/StaticArrays.jl)-Paket zu verwenden. Dieses Paket ermöglicht es Ihnen, solche Arrays auf eine Weise darzustellen, die unnötige Heap-Zuweisungen vermeidet und es dem Compiler ermöglicht, den Code für die *Größe* des Arrays zu optimieren, z.B. durch vollständiges Entrollen von Vektoroperationen (Eliminierung der Schleifen) und das Speichern von Elementen in CPU-Registern.

Zum Beispiel, wenn Sie Berechnungen mit 2D-Geometrien durchführen, haben Sie möglicherweise viele Berechnungen mit 2-Komponenten-Vektoren. Durch die Verwendung des `SVector`-Typs aus StaticArrays.jl können Sie bequeme Vektornotation und Operationen wie `norm(3v - w)` auf den Vektoren `v` und `w` verwenden, während der Compiler den Code so umschreibt, dass er einer minimalen Berechnung entspricht, die gleichbedeutend ist mit `@inbounds hypot(3v[1]-w[1], 3v[2]-w[2])`.

## Avoid string interpolation for I/O

Beim Schreiben von Daten in eine Datei (oder ein anderes I/O-Gerät) ist die Bildung zusätzlicher Zwischenstrings eine Quelle für Overhead. Anstatt:

```julia
println(file, "$a $b")
```

benutzen:

```julia
println(file, a, " ", b)
```

Die erste Version des Codes bildet einen String und schreibt ihn dann in die Datei, während die zweite Version die Werte direkt in die Datei schreibt. Beachten Sie auch, dass in einigen Fällen die String-Interpolation schwerer zu lesen sein kann. Betrachten Sie:

```julia
println(file, "$(f(a))$(f(b))")
```

gegen:

```julia
println(file, f(a), f(b))
```

## Optimize network I/O during parallel execution

Beim Ausführen einer Remote-Funktion parallel:

```julia
using Distributed

responses = Vector{Any}(undef, nworkers())
@sync begin
    for (idx, pid) in enumerate(workers())
        @async responses[idx] = remotecall_fetch(foo, pid, args...)
    end
end
```

ist schneller als:

```julia
using Distributed

refs = Vector{Any}(undef, nworkers())
for (idx, pid) in enumerate(workers())
    refs[idx] = @spawnat pid foo(args...)
end
responses = [fetch(r) for r in refs]
```

Das frühere Ergebnis führt zu einem einzigen Netzwerk-Round-Trip zu jedem Worker, während letzteres zu zwei Netzwerkaufrufen führt - zuerst durch die [`@spawnat`](@ref) und den zweiten aufgrund der [`fetch`](@ref) (oder sogar einer [`wait`](@ref)). Die `4d61726b646f776e2e436f64652822222c202266657463682229_40726566`/`4d61726b646f776e2e436f64652822222c2022776169742229_40726566` wird ebenfalls seriell ausgeführt, was zu einer insgesamt schlechteren Leistung führt.

## Fix deprecation warnings

Eine veraltete Funktion führt intern eine Suche durch, um eine relevante Warnung nur einmal auszugeben. Diese zusätzliche Suche kann zu einer erheblichen Verlangsamung führen, daher sollten alle Verwendungen veralteter Funktionen wie in den Warnungen vorgeschlagen geändert werden.

## Tweaks

Dies sind einige kleinere Punkte, die in engen inneren Schleifen hilfreich sein könnten.

  * Vermeiden Sie unnötige Arrays. Zum Beispiel, anstatt [`sum([x,y,z])`](@ref) verwenden Sie `x+y+z`.
  * Verwenden Sie [`abs2(z)`](@ref) anstelle von [`abs(z)^2`](@ref) für komplexe `z`. Im Allgemeinen versuchen Sie, den Code so umzuschreiben, dass [`abs2`](@ref) anstelle von [`abs`](@ref) für komplexe Argumente verwendet wird.
  * Verwenden Sie [`div(x,y)`](@ref) für die ganzzahlige Truncation-Division anstelle von [`trunc(x/y)`](@ref), [`fld(x,y)`](@ref) anstelle von [`floor(x/y)`](@ref), und [`cld(x,y)`](@ref) anstelle von [`ceil(x/y)`](@ref).

## [Performance Annotations](@id man-performance-annotations)

Manchmal können Sie eine bessere Optimierung ermöglichen, indem Sie bestimmte Programmeigenschaften versprechen.

  * Verwenden Sie [`@inbounds`](@ref), um die Überprüfung der Array-Grenzen innerhalb von Ausdrücken zu eliminieren. Seien Sie sich dessen sicher, bevor Sie dies tun. Wenn die Indizes jemals außerhalb der Grenzen liegen, können Sie Abstürze oder stille Korruption erleiden.
  * Verwenden Sie [`@fastmath`](@ref), um Fließkomma-Optimierungen zuzulassen, die für reelle Zahlen korrekt sind, aber zu Abweichungen bei IEEE-Zahlen führen. Seien Sie vorsichtig, wenn Sie dies tun, da dies die numerischen Ergebnisse ändern kann. Dies entspricht der `-ffast-math`-Option von clang.
  * Schreiben Sie [`@simd`](@ref) vor `for`-Schleifen, um zu versprechen, dass die Iterationen unabhängig sind und umgeordnet werden können. Beachten Sie, dass Julia in vielen Fällen den Code automatisch vektorisieren kann, ohne dass das `@simd`-Makro erforderlich ist; es ist nur in Fällen vorteilhaft, in denen eine solche Transformation sonst illegal wäre, einschließlich Fällen wie der Erlaubnis von Gleitkomma-Neuassoziierung und dem Ignorieren abhängiger Speicherzugriffe (`@simd ivdep`). Seien Sie erneut sehr vorsichtig, wenn Sie `@simd` angeben, da das fälschliche Annotieren einer Schleife mit abhängigen Iterationen zu unerwarteten Ergebnissen führen kann. Insbesondere beachten Sie, dass `setindex!` bei einigen `AbstractArray`-Subtypen von Natur aus von der Iterationsreihenfolge abhängig ist. **Dieses Feature ist experimentell** und könnte sich in zukünftigen Versionen von Julia ändern oder verschwinden.

Die gängige Redewendung, 1:n zu verwenden, um in ein AbstractArray zu indizieren, ist nicht sicher, wenn das Array unkonventionelle Indizes verwendet, und kann zu einem Segmentierungsfehler führen, wenn die Grenzkontrolle deaktiviert ist. Verwenden Sie stattdessen `LinearIndices(x)` oder `eachindex(x)` (siehe auch [Arrays with custom indices](@ref man-custom-indices)).

!!! note
    Während `@simd` direkt vor einer innersten `for`-Schleife platziert werden muss, können sowohl `@inbounds` als auch `@fastmath` auf entweder einzelne Ausdrücke oder alle Ausdrücke angewendet werden, die innerhalb von geschachtelten Codeblöcken erscheinen, z. B. mit `@inbounds begin` oder `@inbounds for ...`.


Hier ist ein Beispiel mit sowohl `@inbounds` als auch `@simd` Markup (wir verwenden hier `@noinline`, um den Optimierer daran zu hindern, zu clever zu sein und unser Benchmark zu untergraben):

```julia
@noinline function inner(x, y)
    s = zero(eltype(x))
    for i=eachindex(x)
        @inbounds s += x[i]*y[i]
    end
    return s
end

@noinline function innersimd(x, y)
    s = zero(eltype(x))
    @simd for i = eachindex(x)
        @inbounds s += x[i] * y[i]
    end
    return s
end

function timeit(n, reps)
    x = rand(Float32, n)
    y = rand(Float32, n)
    s = zero(Float64)
    time = @elapsed for j in 1:reps
        s += inner(x, y)
    end
    println("GFlop/sec        = ", 2n*reps / time*1E-9)
    time = @elapsed for j in 1:reps
        s += innersimd(x, y)
    end
    println("GFlop/sec (SIMD) = ", 2n*reps / time*1E-9)
end

timeit(1000, 1000)
```

Auf einem Computer mit einem 2,4 GHz Intel Core i5-Prozessor ergibt dies:

```
GFlop/sec        = 1.9467069505224963
GFlop/sec (SIMD) = 17.578554163920018
```

(`GFlop/sec` misst die Leistung, und größere Zahlen sind besser.)

Hier ist ein Beispiel mit allen drei Arten von Markup. Dieses Programm berechnet zuerst die endliche Differenz eines eindimensionalen Arrays und bewertet dann die L2-Norm des Ergebnisses:

```julia
function init!(u::Vector)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds @simd for i in 1:n #by asserting that `u` is a `Vector` we can assume it has 1-based indexing
        u[i] = sin(2pi*dx*i)
    end
end

function deriv!(u::Vector, du)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds du[1] = (u[2] - u[1]) / dx
    @fastmath @inbounds @simd for i in 2:n-1
        du[i] = (u[i+1] - u[i-1]) / (2*dx)
    end
    @fastmath @inbounds du[n] = (u[n] - u[n-1]) / dx
end

function mynorm(u::Vector)
    n = length(u)
    T = eltype(u)
    s = zero(T)
    @fastmath @inbounds @simd for i in 1:n
        s += u[i]^2
    end
    @fastmath @inbounds return sqrt(s)
end

function main()
    n = 2000
    u = Vector{Float64}(undef, n)
    init!(u)
    du = similar(u)

    deriv!(u, du)
    nu = mynorm(du)

    @time for i in 1:10^6
        deriv!(u, du)
        nu = mynorm(du)
    end

    println(nu)
end

main()
```

Auf einem Computer mit einem 2,7 GHz Intel Core i7-Prozessor ergibt dies:

```
$ julia wave.jl;
  1.207814709 seconds
4.443986180758249

$ julia --math-mode=ieee wave.jl;
  4.487083643 seconds
4.443986180758249
```

Hier deaktiviert die Option `--math-mode=ieee` das `@fastmath`-Makro, sodass wir die Ergebnisse vergleichen können.

In diesem Fall beträgt die Beschleunigung durch `@fastmath` den Faktor etwa 3,7. Dies ist ungewöhnlich groß – im Allgemeinen wird die Beschleunigung kleiner sein. (In diesem speziellen Beispiel ist der Arbeitsbereich des Benchmarks klein genug, um in den L1-Cache des Prozessors zu passen, sodass die Speicherzugriffsverzögerung keine Rolle spielt und die Rechenzeit von der CPU-Nutzung dominiert wird. In vielen realen Programmen ist dies nicht der Fall.) Außerdem ändert diese Optimierung in diesem Fall nicht das Ergebnis – im Allgemeinen wird das Ergebnis leicht unterschiedlich sein. In einigen Fällen, insbesondere bei numerisch instabilen Algorithmen, kann das Ergebnis sehr unterschiedlich sein.

Die Annotation `@fastmath` reorganisiert Fließkommaausdrücke, z. B. ändert sie die Reihenfolge der Auswertung oder geht davon aus, dass bestimmte Sonderfälle (inf, nan) nicht auftreten können. In diesem Fall (und auf diesem speziellen Computer) besteht der Hauptunterschied darin, dass der Ausdruck `1 / (2*dx)` in der Funktion `deriv` aus der Schleife herausgehoben wird (d. h. außerhalb der Schleife berechnet wird), als hätte man `idx = 1 / (2*dx)` geschrieben. In der Schleife wird der Ausdruck `... / (2*dx)` dann zu `... * idx`, was viel schneller auszuwerten ist. Natürlich hängen sowohl die tatsächliche Optimierung, die vom Compiler angewendet wird, als auch die resultierende Beschleunigung sehr stark von der Hardware ab. Sie können die Änderung im generierten Code untersuchen, indem Sie Julias [`code_native`](@ref) Funktion verwenden.

Beachten Sie, dass `@fastmath` auch davon ausgeht, dass während der Berechnung keine `NaN`s auftreten, was zu überraschendem Verhalten führen kann:

```julia-repl
julia> f(x) = isnan(x);

julia> f(NaN)
true

julia> f_fast(x) = @fastmath isnan(x);

julia> f_fast(NaN)
false
```

## Treat Subnormal Numbers as Zeros

Subnormale Zahlen, früher [denormal numbers](https://en.wikipedia.org/wiki/Denormal_number), sind in vielen Kontexten nützlich, verursachen jedoch auf einigen Hardware eine Leistungseinbuße. Ein Aufruf [`set_zero_subnormals(true)`](@ref) gewährt die Erlaubnis, dass Fließkommaoperationen subnormale Eingaben oder Ausgaben als Null behandeln, was die Leistung auf bestimmter Hardware verbessern kann. Ein Aufruf [`set_zero_subnormals(false)`](@ref) erzwingt striktes IEEE-Verhalten für subnormale Zahlen.

Unten ist ein Beispiel, bei dem Subnormale die Leistung auf bestimmter Hardware merklich beeinflussen:

```julia
function timestep(b::Vector{T}, a::Vector{T}, Δt::T) where T
    @assert length(a)==length(b)
    n = length(b)
    b[1] = 1                            # Boundary condition
    for i=2:n-1
        b[i] = a[i] + (a[i-1] - T(2)*a[i] + a[i+1]) * Δt
    end
    b[n] = 0                            # Boundary condition
end

function heatflow(a::Vector{T}, nstep::Integer) where T
    b = similar(a)
    for t=1:div(nstep,2)                # Assume nstep is even
        timestep(b,a,T(0.1))
        timestep(a,b,T(0.1))
    end
end

heatflow(zeros(Float32,10),2)           # Force compilation
for trial=1:6
    a = zeros(Float32,1000)
    set_zero_subnormals(iseven(trial))  # Odd trials use strict IEEE arithmetic
    @time heatflow(a,1000)
end
```

Dies gibt eine Ausgabe ähnlich wie

```
  0.002202 seconds (1 allocation: 4.063 KiB)
  0.001502 seconds (1 allocation: 4.063 KiB)
  0.002139 seconds (1 allocation: 4.063 KiB)
  0.001454 seconds (1 allocation: 4.063 KiB)
  0.002115 seconds (1 allocation: 4.063 KiB)
  0.001455 seconds (1 allocation: 4.063 KiB)
```

Beachte, wie jede gerade Iteration deutlich schneller ist.

Dieses Beispiel erzeugt viele subnormale Zahlen, da die Werte in `a` eine exponentiell abnehmende Kurve bilden, die sich im Laufe der Zeit langsam abflacht.

Die Behandlung von Subnormalen als Nullen sollte mit Vorsicht erfolgen, da dies einige Identitäten bricht, wie zum Beispiel `x-y == 0` impliziert `x == y`:

```jldoctest
julia> x = 3f-38; y = 2f-38;

julia> set_zero_subnormals(true); (x - y, x == y)
(0.0f0, false)

julia> set_zero_subnormals(false); (x - y, x == y)
(1.0000001f-38, false)
```

In einigen Anwendungen ist eine Alternative zum Nullsetzen von subnormalen Zahlen, ein winziges bisschen Rauschen einzufügen. Zum Beispiel, anstatt `a` mit Nullen zu initialisieren, initialisieren Sie es mit:

```julia
a = rand(Float32,1000) * 1.f-9
```

## [[`@code_warntype`](@ref)](@id man-code-warntype)

Das Makro [`@code_warntype`](@ref) (oder seine Funktionsvariante [`code_warntype`](@ref)) kann manchmal hilfreich sein, um typbezogene Probleme zu diagnostizieren. Hier ist ein Beispiel:

```julia-repl
julia> @noinline pos(x) = x < 0 ? 0 : x;

julia> function f(x)
           y = pos(x)
           return sin(y*x + 1)
       end;

julia> @code_warntype f(3.2)
MethodInstance for f(::Float64)
  from f(x) @ Main REPL[9]:1
Arguments
  #self#::Core.Const(f)
  x::Float64
Locals
  y::Union{Float64, Int64}
Body::Float64
1 ─      (y = Main.pos(x))
│   %2 = (y * x)::Float64
│   %3 = (%2 + 1)::Float64
│   %4 = Main.sin(%3)::Float64
└──      return %4
```

Die Interpretation der Ausgabe von [`@code_warntype`](@ref), ähnlich wie bei seinen Verwandten [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_llvm`](@ref) und [`@code_native`](@ref), erfordert ein wenig Übung. Ihr Code wird in einer Form präsentiert, die auf dem Weg zur Generierung von kompiliertem Maschinencode stark verarbeitet wurde. Die meisten Ausdrücke sind mit einem Typ annotiert, der durch `::T` angezeigt wird (wobei `T` beispielsweise [`Float64`](@ref) sein könnte). Das wichtigste Merkmal von `4d61726b646f776e2e436f64652822222c202240636f64655f7761726e747970652229_40726566` ist, dass nicht-konkrete Typen in ROT angezeigt werden; da dieses Dokument in Markdown verfasst ist, das keine Farben hat, wird in diesem Dokument roter Text durch GROSSBUCHSTABEN dargestellt.

Am oberen Rand wird der abgeleitete Rückgabetyp der Funktion als `Body::Float64` angezeigt. Die nächsten Zeilen repräsentieren den Körper von `f` in Julias SSA-IR-Form. Die nummerierten Kästchen sind Labels und repräsentieren Ziele für Sprünge (über `goto`) in Ihrem Code. Wenn man sich den Körper ansieht, kann man erkennen, dass als erstes `pos` aufgerufen wird und der Rückgabewert als der `Union`-Typ `Union{Float64, Int64}` abgeleitet wurde, der in Großbuchstaben angezeigt wird, da es sich um einen nicht-konkreten Typ handelt. Das bedeutet, dass wir den genauen Rückgabetyp von `pos` basierend auf den Eingabetypen nicht kennen können. Das Ergebnis von `y*x` ist jedoch ein `Float64`, egal ob `y` ein `Float64` oder `Int64` ist. Das Nettoergebnis ist, dass `f(x::Float64)` in seiner Ausgabe nicht typ-instabil sein wird, auch wenn einige der Zwischenberechnungen typ-instabil sind.

Wie Sie diese Informationen nutzen, liegt ganz bei Ihnen. Offensichtlich wäre es am besten, `pos` typstabil zu machen: Wenn Sie dies tun, wären alle Variablen in `f` konkret und ihre Leistung wäre optimal. Es gibt jedoch Umstände, unter denen diese Art von *ephemerer* Typinstabilität nicht allzu sehr ins Gewicht fallen könnte: Wenn `pos` beispielsweise nie isoliert verwendet wird, wird die Tatsache, dass die Ausgabe von `f` typstabil ist (für [`Float64`](@ref) Eingaben), späteren Code vor den propagierenden Effekten der Typinstabilität schützen. Dies ist besonders relevant in Fällen, in denen es schwierig oder unmöglich ist, die Typinstabilität zu beheben. In solchen Fällen sind die oben genannten Tipps (z. B. das Hinzufügen von Typannotationen und/oder das Aufteilen von Funktionen) Ihre besten Werkzeuge, um den "Schaden" durch Typinstabilität zu begrenzen. Beachten Sie auch, dass selbst die Julia-Basis Funktionen hat, die typinstabil sind. Zum Beispiel gibt die Funktion [`findfirst`](@ref) den Index in ein Array zurück, wo ein Schlüssel gefunden wird, oder `nothing`, wenn er nicht gefunden wird, eine klare Typinstabilität. Um es einfacher zu machen, die Typinstabilitäten zu finden, die wahrscheinlich wichtig sind, werden `Union`s, die entweder `missing` oder `nothing` enthalten, in Gelb hervorgehoben, anstatt in Rot.

Die folgenden Beispiele können Ihnen helfen, Ausdrücke zu interpretieren, die als nicht-blattartige Typen gekennzeichnet sind:

  * Funktionstext, der mit `Body::Union{T1,T2})` beginnt

      * Interpretation: Funktion mit instabilem Rückgabewert
      * Vorschlag: Machen Sie den Rückgabewert typstabil, auch wenn Sie ihn annotieren müssen.
  * `invoke Main.g(%%x::Int64)::Union{Float64, Int64}`

      * Interpretation: Aufruf einer typ-instabilen Funktion `g`.
      * Vorschlag: Beheben Sie die Funktion oder annotieren Sie gegebenenfalls den Rückgabewert.
  * `invoke Base.getindex(%%x::Array{Any,1}, 1::Int64)::Any`

      * Interpretation: Zugriff auf Elemente von schlecht typisierten Arrays
      * Vorschlag: Verwenden Sie Arrays mit besser definierten Typen oder annotieren Sie gegebenenfalls den Typ der einzelnen Elementzugriffe.
  * `Base.getfield(%%x, :(:data))::Array{Float64,N} where N`

      * Interpretation: ein Feld zu erhalten, das keinen Blatttyp hat. In diesem Fall hatte der Typ `x`, sagen wir `ArrayContainer`, ein Feld `data::Array{T}`. Aber `Array` benötigt auch die Dimension `N`, um ein konkreter Typ zu sein.
      * Vorschlag: Verwenden Sie konkrete Typen wie `Array{T,3}` oder `Array{T,N}`, wobei `N` jetzt ein Parameter von `ArrayContainer` ist.

## [Performance of captured variable](@id man-performance-captured)

Betrachten Sie das folgende Beispiel, das eine innere Funktion definiert:

```julia
function abmult(r::Int)
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

Die Funktion `abmult` gibt eine Funktion `f` zurück, die ihr Argument mit dem Absolutwert von `r` multipliziert. Die innere Funktion, die `f` zugewiesen ist, wird als "Closure" bezeichnet. Innere Funktionen werden auch von der Sprache für `do`-Blöcke und für Generatorausdrücke verwendet.

Dieser Code-Stil stellt Leistungsherausforderungen für die Sprache dar. Der Parser reorganisiert beim Übersetzen in niedrigere Anweisungen den obigen Code erheblich, indem er die innere Funktion in einen separaten Codeblock extrahiert. "Eingefangene" Variablen wie `r`, die von inneren Funktionen und ihrem umgebenden Geltungsbereich geteilt werden, werden ebenfalls in eine heap-zugewiesene "Box" extrahiert, die sowohl für innere als auch für äußere Funktionen zugänglich ist, da die Sprache vorschreibt, dass `r` im inneren Geltungsbereich identisch mit `r` im äußeren Geltungsbereich sein muss, selbst nachdem der äußere Geltungsbereich (oder eine andere innere Funktion) `r` ändert.

Die Diskussion im vorhergehenden Absatz bezog sich auf den "Parser", das heißt, die Phase der Kompilierung, die stattfindet, wenn das Modul, das `abmult` enthält, zum ersten Mal geladen wird, im Gegensatz zu der späteren Phase, wenn es zum ersten Mal aufgerufen wird. Der Parser "weiß" nicht, dass `Int` ein fester Typ ist oder dass die Anweisung `r = -r` ein `Int` in ein anderes `Int` umwandelt. Die Magie der Typinferenz findet in der späteren Phase der Kompilierung statt.

Somit weiß der Parser nicht, dass `r` einen festen Typ (`Int`) hat, noch dass `r` seinen Wert nicht ändert, sobald die innere Funktion erstellt wird (so dass die Box nicht benötigt wird). Daher erzeugt der Parser Code für eine Box, die ein Objekt mit einem abstrakten Typ wie `Any` enthält, was zur Laufzeit eine Typdispatch für jede Verwendung von `r` erfordert. Dies kann überprüft werden, indem `@code_warntype` auf die obige Funktion angewendet wird. Sowohl das Boxen als auch der Laufzeit-Typdispatch können zu einem Leistungsverlust führen.

Wenn erfasste Variablen in einem leistungskritischen Abschnitt des Codes verwendet werden, helfen die folgenden Tipps, sicherzustellen, dass ihre Verwendung leistungsfähig ist. Zuerst, wenn bekannt ist, dass eine erfasste Variable ihren Typ nicht ändert, kann dies ausdrücklich mit einer Typannotation deklariert werden (auf der Variablen, nicht auf der rechten Seite):

```julia
function abmult2(r0::Int)
    r::Int = r0
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

Die Typannotation stellt teilweise die verlorene Leistung aufgrund der Erfassung wieder her, da der Parser einen konkreten Typ mit dem Objekt in der Box verknüpfen kann. Darüber hinaus kann angezeigt werden, dass die erfasste Variable überhaupt nicht in eine Box gepackt werden muss (da sie nach der Erstellung des Closures nicht mehr neu zugewiesen wird), indem `let`-Blöcke wie folgt verwendet werden.

```julia
function abmult3(r::Int)
    if r < 0
        r = -r
    end
    f = let r = r
            x -> x * r
    end
    return f
end
```

Der `let`-Block erstellt eine neue Variable `r`, deren Gültigkeitsbereich nur die innere Funktion ist. Die zweite Technik stellt die volle Sprachleistung im Beisein von erfassten Variablen wieder her. Beachten Sie, dass dies ein schnelllebiger Aspekt des Compilers ist, und es ist wahrscheinlich, dass zukünftige Versionen nicht diesen Grad an Programmiererannotation erfordern, um Leistung zu erzielen. In der Zwischenzeit automatisieren einige benutzergenerierte Pakete wie [FastClosures](https://github.com/c42f/FastClosures.jl) die Einfügung von `let`-Anweisungen wie in `abmult3`.

## [Multithreading and linear algebra](@id man-multithreading-linear-algebra)

Dieser Abschnitt gilt für mehrsträngige Julia-Code, der in jedem Thread lineare Algebraoperationen durchführt. Tatsächlich beinhalten diese linearen Algebraoperationen BLAS / LAPACK-Aufrufe, die selbst mehrsträngig sind. In diesem Fall muss sichergestellt werden, dass die Kerne aufgrund der beiden verschiedenen Arten von Mehrsträngigkeit nicht überlastet werden.

Julia kompiliert und verwendet eine eigene Kopie von OpenBLAS für lineare Algebra, deren Anzahl an Threads durch die Umgebungsvariable `OPENBLAS_NUM_THREADS` gesteuert wird. Sie kann entweder als Befehlszeilenoption beim Starten von Julia festgelegt oder während der Julia-Sitzung mit `BLAS.set_num_threads(N)` geändert werden (das Untermodul `BLAS` wird durch `using LinearAlgebra` exportiert). Der aktuelle Wert kann mit `BLAS.get_num_threads()` abgerufen werden.

Wenn der Benutzer nichts angibt, versucht Julia, einen angemessenen Wert für die Anzahl der OpenBLAS-Threads auszuwählen (z. B. basierend auf der Plattform, der Julia-Version usw.). Es wird jedoch allgemein empfohlen, den Wert manuell zu überprüfen und festzulegen. Das Verhalten von OpenBLAS ist wie folgt:

  * Wenn `OPENBLAS_NUM_THREADS=1` ist, verwendet OpenBLAS die aufrufenden Julia-Threads, d.h. es "lebt in" dem Julia-Thread, der die Berechnung ausführt.
  * Wenn `OPENBLAS_NUM_THREADS=N>1` ist, erstellt und verwaltet OpenBLAS seinen eigenen Pool von Threads (insgesamt `N`). Es gibt nur einen OpenBLAS-Thread-Pool, der von allen Julia-Threads gemeinsam genutzt wird.

Wenn Sie Julia im Multithreaded-Modus mit `JULIA_NUM_THREADS=X` starten, wird allgemein empfohlen, `OPENBLAS_NUM_THREADS=1` zu setzen. Angesichts des oben beschriebenen Verhaltens kann eine Erhöhung der Anzahl der BLAS-Threads auf `N>1` sehr leicht zu schlechterer Leistung führen, insbesondere wenn `N<<X`. Dies ist jedoch nur eine Faustregel, und der beste Weg, jede Anzahl von Threads festzulegen, besteht darin, in Ihrer spezifischen Anwendung zu experimentieren.

## [Alternative linear algebra backends](@id man-backends-linear-algebra)

Als Alternative zu OpenBLAS gibt es mehrere andere Backends, die bei der Leistung der linearen Algebra helfen können. Prominente Beispiele sind [MKL.jl](https://github.com/JuliaLinearAlgebra/MKL.jl) und [AppleAccelerate.jl](https://github.com/JuliaMath/AppleAccelerate.jl).

Dies sind externe Pakete, daher werden wir sie hier nicht im Detail besprechen. Bitte beziehen Sie sich auf die jeweiligen Dokumentationen (insbesondere, weil sie sich in Bezug auf Multithreading anders verhalten als OpenBLAS).

## Execution latency, package loading and package precompiling time

### Reducing time to first plot etc.

Die erste Zeit, wenn eine Julia-Methode aufgerufen wird, wird sie (und alle Methoden, die sie aufruft, oder die statisch bestimmt werden können) kompiliert. Die [`@time`](@ref) Makrofamilie veranschaulicht dies.

```
julia> foo() = rand(2,2) * rand(2,2)
foo (generic function with 1 method)

julia> @time @eval foo();
  0.252395 seconds (1.12 M allocations: 56.178 MiB, 2.93% gc time, 98.12% compilation time)

julia> @time @eval foo();
  0.000156 seconds (63 allocations: 2.453 KiB)
```

Beachten Sie, dass `@time @eval` besser geeignet ist, um die Kompilierungszeit zu messen, da ohne [`@eval`](@ref) einige Kompilierungen möglicherweise bereits abgeschlossen sind, bevor die Zeitmessung beginnt.

Beim Entwickeln eines Pakets können Sie die Erfahrung Ihrer Benutzer mit *Vorkompilierung* verbessern, sodass der Code, den sie verwenden, bereits kompiliert ist. Um den Paketcode effektiv vorzukompilieren, wird empfohlen, [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) auszuführen, um während der Vorkompilierungszeit eine "Vorkompilierungsarbeitslast" zu erstellen, die repräsentativ für die typische Nutzung des Pakets ist. Dies wird den nativ kompilierten Code im `pkgimage`-Cache des Pakets speichern und die "Zeit bis zur ersten Ausführung" (oft als TTFX bezeichnet) für eine solche Nutzung erheblich reduzieren.

Beachten Sie, dass [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) Arbeitslasten deaktiviert und manchmal über die Einstellungen konfiguriert werden können, wenn Sie nicht die zusätzliche Zeit für die Vorabkompilierung aufwenden möchten, was während der Entwicklung eines Pakets der Fall sein kann.

### Reducing package loading time

Die Ladezeit des Pakets niedrig zu halten, ist in der Regel hilfreich. Allgemeine gute Praktiken für Paketentwickler umfassen:

1. Reduzieren Sie Ihre Abhängigkeiten auf die, die Sie wirklich benötigen. Erwägen Sie die Verwendung von [package extensions](@ref), um die Interoperabilität mit anderen Paketen zu unterstützen, ohne Ihre wesentlichen Abhängigkeiten aufzublähen.
2. Vermeiden Sie die Verwendung von [`__init__()`](@ref)-Funktionen, es sei denn, es gibt keine Alternative, insbesondere solche, die viel Kompilierung auslösen könnten oder einfach lange zum Ausführen benötigen.
3. Wo möglich, beheben Sie [invalidations](https://julialang.org/blog/2020/08/invalidations/) unter Ihren Abhängigkeiten und aus Ihrem Paketcode.

Das Tool [`@time_imports`](@ref) kann im REPL nützlich sein, um die oben genannten Faktoren zu überprüfen.

```julia-repl
julia> @time @time_imports using Plots
      0.5 ms  Printf
     16.4 ms  Dates
      0.7 ms  Statistics
               ┌ 23.8 ms SuiteSparse_jll.__init__() 86.11% compilation time (100% recompilation)
     90.1 ms  SuiteSparse_jll 91.57% compilation time (82% recompilation)
      0.9 ms  Serialization
               ┌ 39.8 ms SparseArrays.CHOLMOD.__init__() 99.47% compilation time (100% recompilation)
    166.9 ms  SparseArrays 23.74% compilation time (100% recompilation)
      0.4 ms  Statistics → SparseArraysExt
      0.5 ms  TOML
      8.0 ms  Preferences
      0.3 ms  PrecompileTools
      0.2 ms  Reexport
... many deps omitted for example ...
      1.4 ms  Tar
               ┌ 73.8 ms p7zip_jll.__init__() 99.93% compilation time (100% recompilation)
     79.4 ms  p7zip_jll 92.91% compilation time (100% recompilation)
               ┌ 27.7 ms GR.GRPreferences.__init__() 99.77% compilation time (100% recompilation)
     43.0 ms  GR 64.26% compilation time (100% recompilation)
               ┌ 2.1 ms Plots.__init__() 91.80% compilation time (100% recompilation)
    300.9 ms  Plots 0.65% compilation time (100% recompilation)
  1.795602 seconds (3.33 M allocations: 190.153 MiB, 7.91% gc time, 39.45% compilation time: 97% of which was recompilation)

```

Beachten Sie, dass in diesem Beispiel mehrere Pakete geladen werden, einige mit `__init__()`-Funktionen, von denen einige eine Kompilierung verursachen, während andere eine Neukompilierung verursachen. Die Neukompilierung wird durch frühere Pakete verursacht, die Methoden ungültig machen. In diesen Fällen, wenn die folgenden Pakete ihre `__init__()`-Funktion ausführen, kommt es bei einigen zu einer Neukompilierung, bevor der Code ausgeführt werden kann.

Darüber hinaus beachten Sie, dass die `Statistics`-Erweiterung `SparseArraysExt` aktiviert wurde, da `SparseArrays` im Abhängigkeitsbaum enthalten ist. d.h. siehe `0.4 ms  Statistics → SparseArraysExt`.

Dieser Bericht bietet eine gute Gelegenheit, zu überprüfen, ob die Kosten der Abhängigkeitsladezeit den Nutzen der Funktionalität rechtfertigen. Auch das `Pkg`-Dienstprogramm `why` kann verwendet werden, um zu berichten, warum eine indirekte Abhängigkeit besteht.

```
(CustomPackage) pkg> why FFMPEG_jll
  Plots → FFMPEG → FFMPEG_jll
  Plots → GR → GR_jll → FFMPEG_jll
```

Um die indirekten Abhängigkeiten zu sehen, die ein Paket mit sich bringt, können Sie `pkg> rm` das Paket entfernen, die Abhängigkeiten sehen, die aus dem Manifest entfernt werden, und dann die Änderung mit `pkg> undo` rückgängig machen.

If loading time is dominated by slow `__init__()` methods having compilation, one verbose way to identify what is being compiled is to use the julia args `--trace-compile=stderr` which will report a [`precompile`](@ref) statement each time a method is compiled. For instance, the full setup would be:

```
$ julia --startup-file=no --trace-compile=stderr
julia> @time @time_imports using CustomPackage
...
```

Beachten Sie die `--startup-file=no`, die hilft, den Test von Paketen zu isolieren, die Sie möglicherweise in Ihrer `startup.jl` haben.

Eine weitere Analyse der Gründe für die Neukompilierung kann mit dem [`SnoopCompile`](https://github.com/timholy/SnoopCompile.jl)-Paket erreicht werden.
