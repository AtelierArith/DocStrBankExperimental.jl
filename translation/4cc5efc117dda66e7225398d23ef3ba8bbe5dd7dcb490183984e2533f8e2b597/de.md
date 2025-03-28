# More about types

Wenn Sie Julia schon eine Weile verwendet haben, verstehen Sie die grundlegende Rolle, die Typen spielen. Hier versuchen wir, einen Blick hinter die Kulissen zu werfen, wobei wir uns besonders auf [Parametric Types](@ref) konzentrieren.

## Types and sets (and `Any` and `Union{}`/`Bottom`)

Es ist vielleicht am einfachsten, Julias Typsystem in Bezug auf Mengen zu begreifen. Während Programme einzelne Werte manipulieren, bezieht sich ein Typ auf eine Menge von Werten. Dies ist nicht dasselbe wie eine Sammlung; zum Beispiel ist ein [`Set`](@ref) von Werten selbst ein einzelner `Set`-Wert. Vielmehr beschreibt ein Typ eine Menge von *möglichen* Werten und drückt Ungewissheit darüber aus, welchen Wert wir haben.

Ein *konkreter* Typ `T` beschreibt die Menge von Werten, deren direkter Tag, wie er von der [`typeof`](@ref)-Funktion zurückgegeben wird, `T` ist. Ein *abstrakter* Typ beschreibt eine möglicherweise größere Menge von Werten.

[`Any`](@ref) beschreibt das gesamte Universum möglicher Werte. [`Integer`](@ref) ist eine Teilmenge von `Any`, die `Int`, [`Int8`](@ref) und andere konkrete Typen umfasst. Intern verwendet Julia auch intensiv einen anderen Typ, der als `Bottom` bekannt ist und auch als `Union{}` geschrieben werden kann. Dies entspricht der leeren Menge.

Julias Typen unterstützen die Standardoperationen der Mengenlehre: Sie können fragen, ob `T1` ein "Teilmenge" (Subtyp) von `T2` ist, mit `T1 <: T2`. Ebenso können Sie zwei Typen mit [`typeintersect`](@ref) schneiden, ihre Vereinigung mit [`Union`](@ref) bilden und einen Typ berechnen, der ihre Vereinigung enthält mit [`typejoin`](@ref):

```jldoctest
julia> typeintersect(Int, Float64)
Union{}

julia> Union{Int, Float64}
Union{Float64, Int64}

julia> typejoin(Int, Float64)
Real

julia> typeintersect(Signed, Union{UInt8, Int8})
Int8

julia> Union{Signed, Union{UInt8, Int8}}
Union{UInt8, Signed}

julia> typejoin(Signed, Union{UInt8, Int8})
Integer

julia> typeintersect(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Int64, Float64}

julia> Union{Tuple{Integer, Float64}, Tuple{Int, Real}}
Union{Tuple{Int64, Real}, Tuple{Integer, Float64}}

julia> typejoin(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Integer, Real}
```

Während diese Operationen abstrakt erscheinen mögen, liegen sie im Herzen von Julia. Zum Beispiel wird die Methodenaufrufsteuerung implementiert, indem durch die Elemente in einer Methodenliste geschritten wird, bis eine erreicht wird, für die der Typ des Argument-Tupels ein Subtyp der Methodensignatur ist. Damit dieser Algorithmus funktioniert, ist es wichtig, dass die Methoden nach ihrer Spezifität sortiert sind und dass die Suche mit den spezifischsten Methoden beginnt. Folglich implementiert Julia auch eine partielle Ordnung auf Typen; dies wird durch eine Funktionalität erreicht, die ähnlich wie `<:` ist, jedoch mit Unterschieden, die weiter unten besprochen werden.

## UnionAll types

Julias Typsystem kann auch einen *iterierten Union* von Typen ausdrücken: eine Vereinigung von Typen über alle Werte einer bestimmten Variablen. Dies ist notwendig, um parametrische Typen zu beschreiben, bei denen die Werte einiger Parameter nicht bekannt sind.

Zum Beispiel hat [`Array`](@ref) zwei Parameter wie in `Array{Int,2}`. Wenn wir den Elementtyp nicht wüssten, könnten wir `Array{T,2} where T` schreiben, was die Vereinigung von `Array{T,2}` für alle Werte von `T` ist: `Union{Array{Int8,2}, Array{Int16,2}, ...}`.

Ein solcher Typ wird durch ein `UnionAll`-Objekt dargestellt, das eine Variable (`T` in diesem Beispiel, vom Typ `TypeVar`) und einen umschlossenen Typ (`Array{T,2}` in diesem Beispiel) enthält.

Betrachten Sie die folgenden Methoden:

```julia
f1(A::Array) = 1
f2(A::Array{Int}) = 2
f3(A::Array{T}) where {T<:Any} = 3
f4(A::Array{Any}) = 4
```

Die Signatur - wie beschrieben in [Function calls](@ref Function-calls) - von `f3` ist ein `UnionAll`-Typ, der einen Tupeltyp umschließt: `Tuple{typeof(f3), Array{T}} where T`. Alle bis auf `f4` können mit `a = [1,2]` aufgerufen werden; alle bis auf `f2` können mit `b = Any[1,2]` aufgerufen werden.

Lass uns diese Typen etwas genauer betrachten:

```jldoctest
julia> dump(Array)
UnionAll
  var: TypeVar
    name: Symbol T
    lb: Union{}
    ub: Any
  body: UnionAll
    var: TypeVar
      name: Symbol N
      lb: Union{}
      ub: Any
    body: Array{T, N} <: DenseArray{T, N}
      ref::MemoryRef{T}
      size::NTuple{N, Int64}
```

Dies zeigt an, dass `Array` tatsächlich einen `UnionAll`-Typ benennt. Es gibt einen `UnionAll`-Typ für jeden Parameter, geschachtelt. Die Syntax `Array{Int,2}` ist äquivalent zu `Array{Int}{2}`; intern wird jeder `UnionAll` mit einem bestimmten Variablenwert instanziiert, einer nach dem anderen, von außen nach innen. Dies verleiht der Auslassung von nachfolgenden Typparametern eine natürliche Bedeutung; `Array{Int}` ergibt einen Typ, der äquivalent zu `Array{Int,N} where N` ist.

Ein `TypeVar` ist selbst kein Typ, sondern sollte als Teil der Struktur eines `UnionAll`-Typs betrachtet werden. Typvariablen haben untere und obere Grenzen für ihre Werte (in den Feldern `lb` und `ub`). Das Symbol `name` ist rein kosmetisch. Intern werden `TypeVar`s nach Adresse verglichen, weshalb sie als veränderbare Typen definiert sind, um sicherzustellen, dass "verschiedene" Typvariablen unterschieden werden können. Allerdings sollten sie aus Konvention nicht verändert werden.

Man kann `TypeVar`s manuell erstellen:

```jldoctest
julia> TypeVar(:V, Signed, Real)
Signed<:V<:Real
```

Es gibt praktische Versionen, die es Ihnen ermöglichen, beliebige dieser Argumente mit Ausnahme des `name`-Symbols wegzulassen.

Die Syntax `Array{T} where T<:Integer` wird zu

```julia
let T = TypeVar(:T,Integer)
    UnionAll(T, Array{T})
end
```

Es ist daher selten notwendig, ein `TypeVar` manuell zu erstellen (tatsächlich sollte dies vermieden werden).

## Free variables

Das Konzept einer *freien* Typvariable ist im Typsystem äußerst wichtig. Wir sagen, dass eine Variable `V` in einem Typ `T` frei ist, wenn `T` nicht das `UnionAll` enthält, das die Variable `V` einführt. Zum Beispiel hat der Typ `Array{Array{V} where V<:Integer}` keine freien Variablen, aber der Teil `Array{V}` darin hat eine freie Variable, `V`.

Ein Typ mit freien Variablen ist, in gewissem Sinne, nicht wirklich ein Typ. Betrachten Sie den Typ `Array{Array{T}} where T`, der sich auf alle homogenen Arrays von Arrays bezieht. Der innere Typ `Array{T}`, der für sich allein betrachtet wird, könnte den Anschein erwecken, sich auf jede Art von Array zu beziehen. Allerdings muss jedes Element des äußeren Arrays den *gleichen* Array-Typ haben, sodass `Array{T}` sich nicht einfach auf irgendein beliebiges Array beziehen kann. Man könnte sagen, dass `Array{T}` effektiv "mehrfach" vorkommt, und `T` muss bei jedem "Vorkommen" den gleichen Wert haben.

Aus diesem Grund ist die Funktion `jl_has_free_typevars` in der C-API sehr wichtig. Typen, für die sie true zurückgibt, liefern keine sinnvollen Antworten bei der Subtypisierung und anderen Typfunktionen.

## TypeNames

Die folgenden zwei [`Array`](@ref) Typen sind funktional äquivalent, drucken jedoch unterschiedlich:

```jldoctest
julia> TV, NV = TypeVar(:T), TypeVar(:N)
(T, N)

julia> Array
Array

julia> Array{TV, NV}
Array{T, N}
```

Diese können unterschieden werden, indem das `name`-Feld des Typs untersucht wird, das ein Objekt des Typs `TypeName` ist:

```julia-repl
julia> dump(Array{Int,1}.name)
TypeName
  name: Symbol Array
  module: Module Core
  names: empty SimpleVector
  wrapper: UnionAll
    var: TypeVar
      name: Symbol T
      lb: Union{}
      ub: Any
    body: UnionAll
      var: TypeVar
        name: Symbol N
        lb: Union{}
        ub: Any
      body: Array{T, N} <: DenseArray{T, N}
  cache: SimpleVector
    ...

  linearcache: SimpleVector
    ...

  hash: Int64 -7900426068641098781
  mt: MethodTable
    name: Symbol Array
    defs: Nothing nothing
    cache: Nothing nothing
    max_args: Int64 0
    module: Module Core
    : Int64 0
    : Int64 0
```

In diesem Fall ist das relevante Feld `wrapper`, das eine Referenz auf den obersten Typ hält, der verwendet wird, um neue `Array`-Typen zu erstellen.

```julia-repl
julia> pointer_from_objref(Array)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array.body.body.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array{TV,NV})
Ptr{Cvoid} @0x00007fcc80c4d930

julia> pointer_from_objref(Array{TV,NV}.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850
```

Das `wrapper`-Feld von [`Array`](@ref) verweist auf sich selbst, aber für `Array{TV,NV}` verweist es zurück auf die ursprüngliche Definition des Typs.

Was ist mit den anderen Feldern? `hash` weist jedem Typ eine Ganzzahl zu. Um das `cache`-Feld zu untersuchen, ist es hilfreich, einen Typ auszuwählen, der weniger häufig verwendet wird als Array. Lassen Sie uns zunächst unseren eigenen Typ erstellen:

```jldoctest
julia> struct MyType{T,N} end

julia> MyType{Int,2}
MyType{Int64, 2}

julia> MyType{Float32, 5}
MyType{Float32, 5}
```

Wenn Sie einen parametrischen Typ instanziieren, wird jeder konkrete Typ im Typ-Cache (`MyType.body.body.name.cache`) gespeichert. Instanzen, die freie Typvariablen enthalten, werden jedoch nicht im Cache gespeichert.

## Tuple types

Tuple-Typen stellen einen interessanten Sonderfall dar. Damit die Dispatch-Funktion bei Deklarationen wie `x::Tuple` funktioniert, muss der Typ in der Lage sein, jedes Tuple zu accommodate. Lassen Sie uns die Parameter überprüfen:

```jldoctest
julia> Tuple
Tuple

julia> Tuple.parameters
svec(Vararg{Any})
```

Im Gegensatz zu anderen Typen sind Tupeltypen in ihren Parametern kovariant, sodass diese Definition `Tuple` erlaubt, mit jedem Typ von Tupel übereinzustimmen:

```jldoctest
julia> typeintersect(Tuple, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{Any}}, Tuple{Int,Float64})
Tuple{Int64, Float64}
```

Wenn jedoch ein variadischer (`Vararg`) Tupeltyp freie Variablen hat, kann er verschiedene Arten von Tupeln beschreiben:

```jldoctest
julia> typeintersect(Tuple{Vararg{T} where T}, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{T}} where T, Tuple{Int,Float64})
Union{}
```

Beachten Sie, dass, wenn `T` in Bezug auf den `Tuple`-Typ frei ist (d.h. seine Bindung `UnionAll`-Typ außerhalb des `Tuple`-Typs liegt), nur ein `T`-Wert über den gesamten Typ funktionieren muss. Daher passt ein heterogener Tuple nicht.

Schließlich ist es erwähnenswert, dass `Tuple{}` unterschiedlich ist:

```jldoctest
julia> Tuple{}
Tuple{}

julia> Tuple{}.parameters
svec()

julia> typeintersect(Tuple{}, Tuple{Int})
Union{}
```

Was ist der "primäre" Tupeltyp?

```julia-repl
julia> pointer_from_objref(Tuple)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{})
Ptr{Cvoid} @0x00007f5998a570d0

julia> pointer_from_objref(Tuple.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{}.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370
```

so `Tuple == Tuple{Vararg{Any}}` ist tatsächlich der primäre Typ.

## Diagonal types

Betrachten Sie den Typ `Tuple{T,T} where T`. Eine Methode mit dieser Signatur würde folgendermaßen aussehen:

```julia
f(x::T, y::T) where {T} = ...
```

Nach der üblichen Interpretation eines `UnionAll`-Typs reicht dieser `T` über alle Typen, einschließlich `Any`, sodass dieser Typ äquivalent zu `Tuple{Any,Any}` sein sollte. Diese Interpretation verursacht jedoch einige praktische Probleme.

Zuerst muss ein Wert von `T` innerhalb der Methodendefinition verfügbar sein. Bei einem Aufruf wie `f(1, 1.0)` ist nicht klar, was `T` sein sollte. Es könnte `Union{Int,Float64}` sein, oder vielleicht [`Real`](@ref). Intuitiv erwarten wir, dass die Deklaration `x::T` bedeutet, dass `T === typeof(x)` ist. Um sicherzustellen, dass diese Invarianz gilt, benötigen wir `typeof(x) === typeof(y) === T` in dieser Methode. Das impliziert, dass die Methode nur für Argumente des genau gleichen Typs aufgerufen werden sollte.

Es stellt sich heraus, dass es sehr nützlich ist, entscheiden zu können, ob zwei Werte denselben Typ haben (dies wird beispielsweise vom Promotionssystem verwendet), sodass wir mehrere Gründe haben, eine andere Interpretation von `Tuple{T,T} where T` haben zu wollen. Um dies zu ermöglichen, fügen wir die folgende Regel zur Subtypisierung hinzu: Wenn eine Variable mehr als einmal in kovarianter Position vorkommt, ist sie darauf beschränkt, nur über konkrete Typen zu variieren. ("Kovariante Position" bedeutet, dass nur `Tuple`- und `Union`-Typen zwischen einem Vorkommen einer Variablen und dem `UnionAll`-Typ, der sie einführt, vorkommen.) Solche Variablen werden als "diagonale Variablen" oder "konkrete Variablen" bezeichnet.

So zum Beispiel kann `Tuple{T,T} where T` als `Union{Tuple{Int8,Int8}, Tuple{Int16,Int16}, ...}` angesehen werden, wobei `T` über alle konkreten Typen variiert. Dies führt zu einigen interessanten Subtyp-Ergebnissen. Zum Beispiel ist `Tuple{Real,Real}` kein Subtyp von `Tuple{T,T} where T`, da es einige Typen wie `Tuple{Int8,Int16}` enthält, bei denen die beiden Elemente unterschiedliche Typen haben. `Tuple{Real,Real}` und `Tuple{T,T} where T` haben die nicht-triviale Schnittmenge `Tuple{T,T} where T<:Real`. Allerdings *ist* `Tuple{Real}` ein Subtyp von `Tuple{T} where T`, da in diesem Fall `T` nur einmal vorkommt und somit nicht diagonal ist.

Als Nächstes betrachten Sie eine Signatur wie die folgende:

```julia
f(a::Array{T}, x::T, y::T) where {T} = ...
```

In diesem Fall tritt `T` in invarianter Position innerhalb von `Array{T}` auf. Das bedeutet, dass der Typ des übergebenen Arrays unmissverständlich den Wert von `T` bestimmt – wir sagen, `T` hat eine *Gleichheitsbeschränkung* darauf. Daher ist in diesem Fall die diagonale Regel nicht wirklich notwendig, da das Array `T` bestimmt und wir dann `x` und `y` beliebige Subtypen von `T` zulassen können. Variablen, die in invarianter Position auftreten, werden niemals als diagonal betrachtet. Diese Verhaltensweise ist leicht umstritten – einige sind der Meinung, dass diese Definition so geschrieben werden sollte wie

```julia
f(a::Array{T}, x::S, y::S) where {T, S<:T} = ...
```

um zu klären, ob `x` und `y` denselben Typ haben müssen. In dieser Version der Signatur müssten sie das, oder wir könnten eine dritte Variable für den Typ von `y` einführen, wenn `x` und `y` unterschiedliche Typen haben können.

Die nächste Komplikation ist die Interaktion von Vereinigungen und diagonalen Variablen, z.B.

```julia
f(x::Union{Nothing,T}, y::T) where {T} = ...
```

Betrachten Sie, was diese Deklaration bedeutet. `y` hat den Typ `T`. `x` kann dann entweder den gleichen Typ `T` haben oder vom Typ [`Nothing`](@ref) sein. Daher sollten alle folgenden Aufrufe übereinstimmen:

```julia
f(1, 1)
f("", "")
f(2.0, 2.0)
f(nothing, 1)
f(nothing, "")
f(nothing, 2.0)
```

Diese Beispiele sagen uns etwas: Wenn `x` `nothing::Nothing` ist, gibt es keine zusätzlichen Einschränkungen für `y`. Es ist, als ob die Methodensignatur `y::Any` hätte. Tatsächlich haben wir die folgende Typäquivalenz:

```julia
(Tuple{Union{Nothing,T},T} where T) == Union{Tuple{Nothing,Any}, Tuple{T,T} where T}
```

Die allgemeine Regel lautet: Eine konkrete Variable in kovarianter Position verhält sich so, als wäre sie nicht konkret, wenn der Subtypisierungsalgorithmus sie nur einmal *verwendet*. Wenn `x` den Typ `Nothing` hat, müssen wir das `T` in `Union{Nothing,T}` nicht verwenden; wir verwenden es nur im zweiten Slot. Dies ergibt sich natürlich aus der Beobachtung, dass es in `Tuple{T} where T` keinen Unterschied macht, `T` auf konkrete Typen einzuschränken; der Typ ist in beiden Fällen gleich `Tuple{Any}`.

Jedoch disqualifiziert das Erscheinen in *invarianter* Position eine Variable davon, konkret zu sein, unabhängig davon, ob diese Variable verwendet wird oder nicht. Andernfalls können Typen unterschiedlich reagieren, je nachdem, mit welchen anderen Typen sie verglichen werden, was die Transitivität von Subtypen beeinträchtigt. Zum Beispiel, betrachten Sie

```julia
Tuple{Int,Int8,Vector{Integer}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

Wenn das `T` innerhalb des `Union` ignoriert wird, dann ist `T` konkret und die Antwort ist "falsch", da die ersten beiden Typen nicht gleich sind. Betrachten Sie stattdessen

```julia
Tuple{Int,Int8,Vector{Any}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

Jetzt können wir das `T` in der `Union` nicht ignorieren (wir müssen haben `T == Any`), also ist `T` nicht konkret und die Antwort ist "wahr". Das würde bedeuten, dass die Konkretheit von `T` von dem anderen Typ abhängt, was nicht akzeptabel ist, da ein Typ eine klare Bedeutung für sich selbst haben muss. Daher wird das Auftreten von `T` innerhalb von `Vector` in beiden Fällen berücksichtigt.

## Subtyping diagonal variables

Der Subtypisierungsalgorithmus für diagonale Variablen hat zwei Komponenten: (1) Identifizierung von Variablenvorkommen und (2) Sicherstellung, dass diagonale Variablen nur über konkrete Typen reichen.

Die erste Aufgabe wird erfüllt, indem Zähler `occurs_inv` und `occurs_cov` (in `src/subtype.c`) für jede Variable in der Umgebung geführt werden, die Anzahl der invarianten und kovarianten Vorkommen zu verfolgen. Eine Variable ist diagonal, wenn `occurs_inv == 0 && occurs_cov > 1`.

Die zweite Aufgabe wird erfüllt, indem eine Bedingung an die Untergrenze einer Variablen auferlegt wird. Während der Subtypisierungsalgorithmus läuft, verengt er die Grenzen jeder Variablen (erhöht die Untergrenzen und senkt die Obergrenzen), um den Bereich der Variablenwerte zu verfolgen, für den die Subtypbeziehung gelten würde. Wenn wir die Auswertung des Körpers eines `UnionAll`-Typs abgeschlossen haben, dessen Variable diagonal ist, betrachten wir die endgültigen Werte der Grenzen. Da die Variable konkret sein muss, tritt ein Widerspruch auf, wenn ihre Untergrenze kein Subtyp eines konkreten Typs sein könnte. Zum Beispiel kann ein abstrakter Typ wie [`AbstractArray`](@ref) kein Subtyp eines konkreten Typs sein, aber ein konkreter Typ wie `Int` kann es sein, und der leere Typ `Bottom` kann es ebenfalls sein. Wenn eine Untergrenze diesen Test nicht besteht, stoppt der Algorithmus mit der Antwort `false`.

Zum Beispiel, im Problem `Tuple{Int,String} <: Tuple{T,T} where T` leiten wir ab, dass dies wahr wäre, wenn `T` ein Supertyp von `Union{Int,String}` wäre. Allerdings ist `Union{Int,String}` ein abstrakter Typ, sodass die Beziehung nicht gilt.

Dieser Konkretheitstest wird durch die Funktion `is_leaf_bound` durchgeführt. Beachten Sie, dass dieser Test leicht von `jl_is_leaf_type` abweicht, da er auch für `Bottom` `true` zurückgibt. Derzeit ist diese Funktion heuristisch und erfasst nicht alle möglichen konkreten Typen. Die Schwierigkeit besteht darin, dass es davon abhängt, ob eine Untergrenze konkret ist, welche Werte die Grenzen anderer Typvariablen haben. Zum Beispiel ist `Vector{T}` nur dann äquivalent zum konkreten Typ `Vector{Int}`, wenn sowohl die oberen als auch die unteren Grenzen von `T` gleich `Int` sind. Wir haben noch keinen vollständigen Algorithmus dafür ausgearbeitet.

## Introduction to the internal machinery

Die meisten Operationen zur Behandlung von Typen finden sich in den Dateien `jltypes.c` und `subtype.c`. Ein guter Ausgangspunkt ist, das Subtyping in Aktion zu beobachten. Bauen Sie Julia mit `make debug` und starten Sie Julia innerhalb eines Debuggers. [gdb debugging tips](@ref gdb-debugging-tips) enthält einige nützliche Tipps.

Da der Subtypisierungs-Code stark im REPL selbst verwendet wird – und daher Breakpoints in diesem Code häufig ausgelöst werden – wird es am einfachsten sein, wenn Sie die folgende Definition erstellen:

```julia-repl
julia> function mysubtype(a,b)
           ccall(:jl_breakpoint, Cvoid, (Any,), nothing)
           a <: b
       end
```

und setzen Sie dann einen Haltepunkt in `jl_breakpoint`. Sobald dieser Haltepunkt ausgelöst wird, können Sie Haltepunkte in anderen Funktionen setzen.

Als Aufwärmübung versuche Folgendes:

```julia
mysubtype(Tuple{Int, Float64}, Tuple{Integer, Real})
```

Wir können es interessanter gestalten, indem wir einen komplexeren Fall ausprobieren:

```julia
mysubtype(Tuple{Array{Int,2}, Int8}, Tuple{Array{T}, T} where T)
```

## Subtyping and method sorting

Die `type_morespecific`-Funktionen werden verwendet, um eine partielle Ordnung auf Funktionen in Methodentabellen (von am spezifischsten bis am wenigsten spezifisch) aufzuerlegen. Die Spezifität ist strikt; wenn `a` spezifischer ist als `b`, dann ist `a` nicht gleich `b` und `b` ist nicht spezifischer als `a`.

Wenn `a` ein strenger Subtyp von `b` ist, wird es automatisch als spezifischer betrachtet. Von dort aus verwendet `type_morespecific` einige weniger formale Regeln. Zum Beispiel ist `subtype` empfindlich gegenüber der Anzahl der Argumente, aber `type_morespecific` möglicherweise nicht. Insbesondere ist `Tuple{Int,AbstractFloat}` spezifischer als `Tuple{Integer}`, auch wenn es kein Subtyp ist. (Von `Tuple{Int,AbstractFloat}` und `Tuple{Integer,Float64}` ist keiner spezifischer als der andere.) Ebenso ist `Tuple{Int,Vararg{Int}}` kein Subtyp von `Tuple{Integer}`, wird aber als spezifischer betrachtet. Allerdings erhält `morespecific` einen Bonus für die Länge: Insbesondere ist `Tuple{Int,Int}` spezifischer als `Tuple{Int,Vararg{Int}}`.

Wenn Sie debuggen, wie Methoden sortiert werden, kann es praktisch sein, die Funktion zu definieren:

```julia
type_morespecific(a, b) = ccall(:jl_type_morespecific, Cint, (Any,Any), a, b)
```

was es Ihnen ermöglicht zu testen, ob der Tupeltyp `a` spezifischer ist als der Tupeltyp `b`.
