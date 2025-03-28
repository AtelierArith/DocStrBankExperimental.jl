# Methods

Erinnere dich an [Functions](@ref man-functions), dass eine Funktion ein Objekt ist, das ein Tupel von Argumenten auf einen Rückgabewert abbildet oder eine Ausnahme auslöst, wenn kein geeigneter Wert zurückgegeben werden kann. Es ist üblich, dass dieselbe konzeptionelle Funktion oder Operation für verschiedene Arten von Argumenten ganz unterschiedlich implementiert wird: Das Addieren von zwei Ganzzahlen ist sehr unterschiedlich vom Addieren von zwei Gleitkommazahlen, die beide von der Addition einer Ganzzahl zu einer Gleitkommazahl unterschieden werden. Trotz ihrer Implementierungsunterschiede fallen diese Operationen alle unter das allgemeine Konzept der "Addition". Dementsprechend gehören in Julia all diese Verhaltensweisen zu einem einzigen Objekt: der `+` Funktion.

Um die Verwendung vieler verschiedener Implementierungen desselben Konzepts reibungslos zu gestalten, müssen Funktionen nicht alle auf einmal definiert werden, sondern können stückweise definiert werden, indem spezifische Verhaltensweisen für bestimmte Kombinationen von Argumenttypen und -anzahlen bereitgestellt werden. Eine Definition eines möglichen Verhaltens für eine Funktion wird als *Methode* bezeichnet. Bisher haben wir nur Beispiele für Funktionen präsentiert, die mit einer einzigen Methode definiert sind, die für alle Argumenttypen anwendbar ist. Die Signaturen von Methodendefinitionen können jedoch annotiert werden, um die Typen der Argumente zusätzlich zu ihrer Anzahl anzugeben, und es kann mehr als eine einzige Methodendefinition bereitgestellt werden. Wenn eine Funktion auf ein bestimmtes Tupel von Argumenten angewendet wird, wird die spezifischste Methode angewendet, die auf diese Argumente anwendbar ist. Das Gesamtverhalten einer Funktion ist somit ein Flickwerk der Verhaltensweisen ihrer verschiedenen Methodendefinitionen. Wenn das Flickwerk gut gestaltet ist, wird das äußere Verhalten der Funktion, obwohl die Implementierungen der Methoden sehr unterschiedlich sein können, nahtlos und konsistent erscheinen.

Die Wahl, welche Methode ausgeführt werden soll, wenn eine Funktion angewendet wird, wird als *Dispatch* bezeichnet. Julia ermöglicht es dem Dispatch-Prozess, auszuwählen, welche der Methoden einer Funktion aufgerufen werden soll, basierend auf der Anzahl der übergebenen Argumente und den Typen aller Argumente der Funktion. Dies unterscheidet sich von traditionellen objektorientierten Sprachen, in denen der Dispatch nur auf dem ersten Argument basiert, das oft eine spezielle Argument-Syntax hat und manchmal implizit statt explizit als Argument geschrieben wird. [^1] Die Verwendung aller Argumente einer Funktion, um auszuwählen, welche Methode aufgerufen werden soll, anstatt nur des ersten, wird als [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch) bezeichnet. Mehrfach-Dispatch ist besonders nützlich für mathematische Codes, wo es wenig Sinn macht, die Operationen künstlich einem Argument mehr zuzuordnen als den anderen: Gehört die Additionsoperation in `x + y` mehr zu `x` als zu `y`? Die Implementierung eines mathematischen Operators hängt im Allgemeinen von den Typen aller seiner Argumente ab. Selbst über mathematische Operationen hinaus erweist sich jedoch der Mehrfach-Dispatch als kraftvolles und praktisches Paradigma zur Strukturierung und Organisation von Programmen.

[^1]: In C++ or Java, for example, in a method call like `obj.meth(arg1,arg2)`, the object obj "receives" the method call and is implicitly passed to the method via the `this` keyword, rather than as an explicit method argument. When the current `this` object is the receiver of a method call, it can be omitted altogether, writing just `meth(arg1,arg2)`, with `this` implied as the receiving object.

!!! note
    Alle Beispiele in diesem Kapitel gehen davon aus, dass Sie Methoden für eine Funktion im *gleichen* Modul definieren. Wenn Sie Methoden zu einer Funktion in einem *anderen* Modul hinzufügen möchten, müssen Sie sie `importieren` oder den Namen qualifiziert mit Modulnamen verwenden. Siehe den Abschnitt über [namespace management](@ref namespace-management).


## Defining Methods

Bis jetzt haben wir in unseren Beispielen nur Funktionen mit einer einzelnen Methode definiert, die keine Einschränkungen bei den Argumenttypen haben. Solche Funktionen verhalten sich genau wie in traditionellen dynamisch typisierten Sprachen. Dennoch haben wir mehrfach Dispatch und Methoden fast kontinuierlich verwendet, ohne es zu bemerken: Alle standardmäßigen Funktionen und Operatoren von Julia, wie die zuvor erwähnte `+`-Funktion, haben viele Methoden, die ihr Verhalten über verschiedene mögliche Kombinationen von Argumenttyp und -anzahl definieren.

Beim Definieren einer Funktion kann man optional die Typen der Parameter, auf die sie anwendbar ist, mit dem `::` Typ-Assertionsoperator einschränken, der im Abschnitt über [Composite Types](@ref) eingeführt wurde:

```jldoctest fofxy
julia> f(x::Float64, y::Float64) = 2x + y
f (generic function with 1 method)
```

Diese Funktionsdefinition gilt nur für Aufrufe, bei denen `x` und `y` beide Werte des Typs [`Float64`](@ref) sind:

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0
```

Die Anwendung auf andere Arten von Argumenten führt zu einem [`MethodError`](@ref):

```jldoctest fofxy
julia> f(2.0, 3)
ERROR: MethodError: no method matching f(::Float64, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(Float32(2.0), 3.0)
ERROR: MethodError: no method matching f(::Float32, ::Float64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, ::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(2.0, "3.0")
ERROR: MethodError: no method matching f(::Float64, ::String)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f("2.0", "3.0")
ERROR: MethodError: no method matching f(::String, ::String)
The function `f` exists, but no method is defined for this combination of argument types.
```

Wie Sie sehen können, müssen die Argumente genau vom Typ [`Float64`](@ref) sein. Andere numerische Typen, wie Ganzzahlen oder 32-Bit-Gleitkommawerte, werden nicht automatisch in 64-Bit-Gleitkommawerte konvertiert, noch werden Zeichenfolgen als Zahlen geparst. Da `Float64` ein konkreter Typ ist und konkrete Typen in Julia nicht unterklassenfähig sind, kann eine solche Definition nur auf Argumente angewendet werden, die genau vom Typ `Float64` sind. Es kann jedoch oft nützlich sein, allgemeinere Methoden zu schreiben, bei denen die deklarierten Parametertypen abstrakt sind:

```jldoctest fofxy
julia> f(x::Number, y::Number) = 2x - y
f (generic function with 2 methods)

julia> f(2.0, 3)
1.0
```

Diese Methodendefinition gilt für jedes Paar von Argumenten, die Instanzen von [`Number`](@ref) sind. Sie müssen nicht vom gleichen Typ sein, solange sie jeweils numerische Werte sind. Das Problem der Handhabung unterschiedlicher numerischer Typen wird den arithmetischen Operationen im Ausdruck `2x - y` überlassen.

Um eine Funktion mit mehreren Methoden zu definieren, definiert man die Funktion einfach mehrmals mit unterschiedlichen Zahlen und Typen von Argumenten. Die erste Methodenbeschreibung für eine Funktion erstellt das Funktionsobjekt, und nachfolgende Methodenbeschreibungen fügen neue Methoden zum bestehenden Funktionsobjekt hinzu. Die spezifischste Methodenbeschreibung, die mit der Anzahl und den Typen der Argumente übereinstimmt, wird ausgeführt, wenn die Funktion angewendet wird. Somit definieren die beiden oben genannten Methodenbeschreibungen zusammen das Verhalten für `f` über alle Paare von Instanzen des abstrakten Typs `Number` – jedoch mit einem anderen Verhalten, das spezifisch für Paare von [`Float64`](@ref) Werten ist. Wenn eines der Argumente ein 64-Bit-Gleitkommawert ist, das andere jedoch nicht, kann die Methode `f(Float64,Float64)` nicht aufgerufen werden und die allgemeinere Methode `f(Number,Number)` muss verwendet werden:

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0

julia> f(2, 3.0)
1.0

julia> f(2.0, 3)
1.0

julia> f(2, 3)
1
```

The `2x + y` definition is only used in the first case, while the `2x - y` definition is used in the others. No automatic casting or conversion of function arguments is ever performed: all conversion in Julia is non-magical and completely explicit. [Conversion and Promotion](@ref conversion-and-promotion), however, shows how clever application of sufficiently advanced technology can be indistinguishable from magic. [^Clarke61]

Für nicht-numerische Werte und für weniger oder mehr als zwei Argumente bleibt die Funktion `f` undefiniert, und ihre Anwendung führt weiterhin zu einem [`MethodError`](@ref):

```jldoctest fofxy
julia> f("foo", 3)
ERROR: MethodError: no method matching f(::String, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Number, ::Number)
   @ Main none:1
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f()
ERROR: MethodError: no method matching f()
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1
  f(!Matched::Number, !Matched::Number)
   @ Main none:1

Stacktrace:
[...]
```

Sie können leicht sehen, welche Methoden für ein Funktion existieren, indem Sie das Funktionsobjekt selbst in einer interaktiven Sitzung eingeben:

```jldoctest fofxy
julia> f
f (generic function with 2 methods)
```

Dieser Output sagt uns, dass `f` ein Funktionsobjekt mit zwei Methoden ist. Um herauszufinden, wie die Signaturen dieser Methoden aussehen, verwenden Sie die [`methods`](@ref) Funktion:

```jldoctest fofxy
julia> methods(f)
# 2 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
```

was zeigt, dass `f` zwei Methoden hat, eine, die zwei `Float64`-Argumente entgegennimmt, und eine, die Argumente vom Typ `Number` entgegennimmt. Es wird auch die Datei und die Zeilennummer angezeigt, an der die Methoden definiert wurden: Da diese Methoden im REPL definiert wurden, erhalten wir die scheinbare Zeilennummer `none:1`.

In Abwesenheit einer Typdeklaration mit `::` ist der Typ eines Methodenparameters standardmäßig `Any`, was bedeutet, dass er nicht eingeschränkt ist, da alle Werte in Julia Instanzen des abstrakten Typs `Any` sind. Daher können wir eine Auffangmethode für `f` wie folgt definieren:

```jldoctest fofxy
julia> f(x,y) = println("Whoa there, Nelly.")
f (generic function with 3 methods)

julia> methods(f)
# 3 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
 [3] f(x, y)
     @ none:1

julia> f("foo", 1)
Whoa there, Nelly.
```

Dieser Catch-All ist weniger spezifisch als jede andere mögliche Methodenbeschreibung für ein Paar von Parameterwerten, sodass er nur für Argumentpaare aufgerufen wird, auf die keine andere Methodenbeschreibung zutrifft.

Beachten Sie, dass in der Signatur der dritten Methode kein Typ für die Argumente `x` und `y` angegeben ist. Dies ist eine verkürzte Art, `f(x::Any, y::Any)` auszudrücken.

Obwohl es ein einfaches Konzept zu sein scheint, ist die Mehrfachdispatch auf die Typen von Werten vielleicht das mächtigste und zentrale Merkmal der Programmiersprache Julia. Kernoperationen haben typischerweise Dutzende von Methoden:

```julia-repl
julia> methods(+)
# 180 methods for generic function "+":
[1] +(x::Bool, z::Complex{Bool}) in Base at complex.jl:227
[2] +(x::Bool, y::Bool) in Base at bool.jl:89
[3] +(x::Bool) in Base at bool.jl:86
[4] +(x::Bool, y::T) where T<:AbstractFloat in Base at bool.jl:96
[5] +(x::Bool, z::Complex) in Base at complex.jl:234
[6] +(a::Float16, b::Float16) in Base at float.jl:373
[7] +(x::Float32, y::Float32) in Base at float.jl:375
[8] +(x::Float64, y::Float64) in Base at float.jl:376
[9] +(z::Complex{Bool}, x::Bool) in Base at complex.jl:228
[10] +(z::Complex{Bool}, x::Real) in Base at complex.jl:242
[11] +(x::Char, y::Integer) in Base at char.jl:40
[12] +(c::BigInt, x::BigFloat) in Base.MPFR at mpfr.jl:307
[13] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt, e::BigInt) in Base.GMP at gmp.jl:392
[14] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt) in Base.GMP at gmp.jl:391
[15] +(a::BigInt, b::BigInt, c::BigInt) in Base.GMP at gmp.jl:390
[16] +(x::BigInt, y::BigInt) in Base.GMP at gmp.jl:361
[17] +(x::BigInt, c::Union{UInt16, UInt32, UInt64, UInt8}) in Base.GMP at gmp.jl:398
...
[180] +(a, b, c, xs...) in Base at operators.jl:424
```

Mehrfachdispatch zusammen mit dem flexiblen parametrischen Typsystem verleiht Julia die Fähigkeit, hochgradig abstrakte Algorithmen auszudrücken, die von Implementierungsdetails entkoppelt sind.

## [Method specializations](@id man-method-specializations)

Wenn Sie mehrere Methoden derselben Funktion erstellen, wird dies manchmal als "Spezialisierung" bezeichnet. In diesem Fall spezialisieren Sie die *Funktion*, indem Sie zusätzliche Methoden hinzufügen: jede neue Methode ist eine neue Spezialisierung der Funktion. Wie oben gezeigt, werden diese Spezialisierungen von `methods` zurückgegeben.

Es gibt eine andere Art der Spezialisierung, die ohne Eingreifen des Programmierers erfolgt: Der Compiler von Julia kann die *Methode* automatisch für die spezifischen verwendeten Argumenttypen spezialisieren. Solche Spezialisierungen werden *nicht* von `methods` aufgelistet, da dies keine neuen `Method`s erstellt, aber Tools wie [`@code_typed`](@ref) ermöglichen es Ihnen, solche Spezialisierungen zu inspizieren.

Zum Beispiel, wenn Sie eine Methode erstellen

```
mysum(x::Real, y::Real) = x + y
```

du hast der Funktion `mysum` eine neue Methode (möglicherweise ihre einzige Methode) gegeben, und diese Methode nimmt ein beliebiges Paar von `Real`-Zahlen als Eingaben. Aber wenn du dann ausführst

```julia-repl
julia> mysum(1, 2)
3

julia> mysum(1.0, 2.0)
3.0
```

Julia wird `mysum` zweimal kompilieren, einmal für `x::Int, y::Int` und erneut für `x::Float64, y::Float64`. Der Grund für die doppelte Kompilierung ist die Leistung: Die Methoden, die für `+` (das `mysum` verwendet) aufgerufen werden, variieren je nach den spezifischen Typen von `x` und `y`, und durch die Kompilierung unterschiedlicher Spezialisierungen kann Julia die gesamte Methoden-Suche im Voraus durchführen. Dies ermöglicht es dem Programm, viel schneller zu laufen, da es sich während der Ausführung nicht mit der Methoden-Suche beschäftigen muss. Julias automatische Spezialisierung ermöglicht es Ihnen, generische Algorithmen zu schreiben und zu erwarten, dass der Compiler effizienten, spezialisierten Code generiert, um jeden benötigten Fall zu behandeln.

In Fällen, in denen die Anzahl potenzieller Spezialisierungen effektiv unbegrenzt sein könnte, kann Julia diese Standard-Spezialisierung vermeiden. Siehe [Be aware of when Julia avoids specializing](@ref) für weitere Informationen.

## [Method Ambiguities](@id man-ambiguities)

Es ist möglich, eine Menge von Funktionsmethoden zu definieren, sodass es für einige Kombinationen von Argumenten keine eindeutige spezifischste Methode gibt:

```jldoctest gofxy
julia> g(x::Float64, y) = 2x + y
g (generic function with 1 method)

julia> g(x, y::Float64) = x + 2y
g (generic function with 2 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
ERROR: MethodError: g(::Float64, ::Float64) is ambiguous.

Candidates:
  g(x, y::Float64)
    @ Main none:1
  g(x::Float64, y)
    @ Main none:1

Possible fix, define
  g(::Float64, ::Float64)

Stacktrace:
[...]
```

Hier könnte der Aufruf `g(2.0, 3.0)` entweder von der Methode `g(::Float64, ::Any)` oder der Methode `g(::Any, ::Float64)` behandelt werden. Die Reihenfolge, in der die Methoden definiert sind, spielt keine Rolle und keine ist spezifischer als die andere. In solchen Fällen wirft Julia eine [`MethodError`](@ref), anstatt willkürlich eine Methode auszuwählen. Sie können Methodenambiguitäten vermeiden, indem Sie eine geeignete Methode für den Schnittmengenfall angeben:

```jldoctest gofxy
julia> g(x::Float64, y::Float64) = 2x + 2y
g (generic function with 3 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
10.0
```

Es wird empfohlen, dass die disambiguierende Methode zuerst definiert wird, da ansonsten die Mehrdeutigkeit besteht, wenn auch nur vorübergehend, bis die spezifischere Methode definiert ist.

In komplexeren Fällen beinhaltet die Auflösung von Methodenambiguitäten ein gewisses Element des Designs; dieses Thema wird weiter untersucht [below](@ref man-method-design-ambiguities).

## Parametric Methods

Methoden-Definitionen können optional Typ-Parameter haben, die die Signatur qualifizieren:

```jldoctest same_typefunc
julia> same_type(x::T, y::T) where {T} = true
same_type (generic function with 1 method)

julia> same_type(x,y) = false
same_type (generic function with 2 methods)
```

Die erste Methode wird angewendet, wenn beide Argumente vom gleichen konkreten Typ sind, unabhängig davon, welcher Typ das ist, während die zweite Methode als Auffangnetz fungiert und alle anderen Fälle abdeckt. Insgesamt definiert dies also eine boolesche Funktion, die überprüft, ob ihre beiden Argumente vom gleichen Typ sind:

```jldoctest same_typefunc
julia> same_type(1, 2)
true

julia> same_type(1, 2.0)
false

julia> same_type(1.0, 2.0)
true

julia> same_type("foo", 2.0)
false

julia> same_type("foo", "bar")
true

julia> same_type(Int32(1), Int64(2))
false
```

Solche Definitionen entsprechen Methoden, deren Typsignaturen `UnionAll`-Typen sind (siehe [UnionAll Types](@ref)).

Diese Art der Definition des Funktionsverhaltens durch Dispatch ist in Julia recht verbreitet – sogar idiomatisch. Die Typparameter von Methoden sind nicht darauf beschränkt, als Typen von Argumenten verwendet zu werden: Sie können überall dort verwendet werden, wo ein Wert in der Signatur der Funktion oder im Funktionskörper stehen würde. Hier ist ein Beispiel, bei dem der Typparameter der Methode `T` als Typparameter für den parametrischen Typ `Vector{T}` in der Methodensignatur verwendet wird:

```jldoctest
julia> function myappend(v::Vector{T}, x::T) where {T}
           return [v..., x]
       end
myappend (generic function with 1 method)
```

Der Typparameter `T` in diesem Beispiel stellt sicher, dass das hinzugefügte Element `x` ein Subtyp des bestehenden eltype des Vektors `v` ist. Das Schlüsselwort `where` führt eine Liste dieser Einschränkungen nach der Methodensignaturdefinition ein. Dies funktioniert genauso für einzeilige Definitionen, wie oben gesehen, und muss *vor* der [return type declaration](@ref man-functions-return-type) erscheinen, falls vorhanden, wie unten dargestellt:

```jldoctest
julia> (myappend(v::Vector{T}, x::T)::Vector) where {T} = [v..., x]
myappend (generic function with 1 method)

julia> myappend([1,2,3],4)
4-element Vector{Int64}:
 1
 2
 3
 4

julia> myappend([1,2,3],2.5)
ERROR: MethodError: no method matching myappend(::Vector{Int64}, ::Float64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]

julia> myappend([1.0,2.0,3.0],4.0)
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0

julia> myappend([1.0,2.0,3.0],4)
ERROR: MethodError: no method matching myappend(::Vector{Float64}, ::Int64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]
```

Wenn der Typ des angehängten Elements nicht mit dem Elementtyp des Vektors übereinstimmt, wird ein [`MethodError`](@ref) ausgelöst. Im folgenden Beispiel wird der Typparameter `T` der Methode als Rückgabewert verwendet:

```jldoctest
julia> mytypeof(x::T) where {T} = T
mytypeof (generic function with 1 method)

julia> mytypeof(1)
Int64

julia> mytypeof(1.0)
Float64
```

Genau wie Sie Subtypbeschränkungen für Typparameter in Typdeklarationen festlegen können (siehe [Parametric Types](@ref)), können Sie auch Typparameter von Methoden einschränken:

```jldoctest
julia> same_type_numeric(x::T, y::T) where {T<:Number} = true
same_type_numeric (generic function with 1 method)

julia> same_type_numeric(x::Number, y::Number) = false
same_type_numeric (generic function with 2 methods)

julia> same_type_numeric(1, 2)
true

julia> same_type_numeric(1, 2.0)
false

julia> same_type_numeric(1.0, 2.0)
true

julia> same_type_numeric("foo", 2.0)
ERROR: MethodError: no method matching same_type_numeric(::String, ::Float64)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  same_type_numeric(!Matched::T, ::T) where T<:Number
   @ Main none:1
  same_type_numeric(!Matched::Number, ::Number)
   @ Main none:1

Stacktrace:
[...]

julia> same_type_numeric("foo", "bar")
ERROR: MethodError: no method matching same_type_numeric(::String, ::String)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

julia> same_type_numeric(Int32(1), Int64(2))
false
```

Die `same_type_numeric`-Funktion verhält sich ähnlich wie die oben definierte `same_type`-Funktion, ist jedoch nur für Zahlenpaare definiert.

Parametrische Methoden erlauben die gleiche Syntax wie `where`-Ausdrücke, die zur Definition von Typen verwendet werden (siehe [UnionAll Types](@ref)). Wenn es nur einen einzigen Parameter gibt, können die umschließenden geschweiften Klammern (in `where {T}`) weggelassen werden, werden jedoch oft zur Klarheit bevorzugt. Mehrere Parameter können durch Kommas getrennt werden, z. B. `where {T, S<:Real}`, oder mit geschachtelten `where`-Ausdrücken geschrieben werden, z. B. `where S<:Real where T`.

## Redefining Methods

Wenn Sie eine Methode neu definieren oder neue Methoden hinzufügen, ist es wichtig zu erkennen, dass diese Änderungen nicht sofort wirksam werden. Dies ist entscheidend für Julias Fähigkeit, Code statisch zu inferieren und zu kompilieren, um schnell zu laufen, ohne die üblichen JIT-Tricks und -Überhead. Tatsächlich wird keine neue Methodendefinition für die aktuelle Laufzeitumgebung sichtbar sein, einschließlich Tasks und Threads (und aller zuvor definierten `@generated` Funktionen). Lassen Sie uns mit einem Beispiel beginnen, um zu sehen, was das bedeutet:

```julia-repl
julia> function tryeval()
           @eval newfun() = 1
           newfun()
       end
tryeval (generic function with 1 method)

julia> tryeval()
ERROR: MethodError: no method matching newfun()
The applicable method may be too new: running in world age xxxx1, while current world is xxxx2.
Closest candidates are:
  newfun() at none:1 (method too new to be called from this world context.)
 in tryeval() at none:1
 ...

julia> newfun()
1
```

In diesem Beispiel ist zu beobachten, dass die neue Definition für `newfun` erstellt wurde, aber nicht sofort aufgerufen werden kann. Die neue globale Variable ist sofort für die Funktion `tryeval` sichtbar, sodass Sie `return newfun` (ohne Klammern) schreiben könnten. Aber weder Sie noch einer Ihrer Aufrufer noch die Funktionen, die sie aufrufen, usw. können diese neue Methodendefinition aufrufen!

Aber es gibt eine Ausnahme: Zukünftige Aufrufe von `newfun` *aus dem REPL* funktionieren wie erwartet, da sie sowohl die neue Definition von `newfun` sehen als auch aufrufen können.

Zukünftige Aufrufe von `tryeval` werden jedoch die Definition von `newfun` so sehen, wie sie *zum vorherigen Befehl im REPL* war, und somit vor diesem Aufruf von `tryeval`.

Vielleicht möchten Sie dies selbst ausprobieren, um zu sehen, wie es funktioniert.

Die Implementierung dieses Verhaltens ist ein "Weltalterzähler". Dieser monoton steigende Wert verfolgt jede Methode-Definitionsoperation. Dies ermöglicht es, "die Menge der Methoden-Definitionen, die in einer bestimmten Laufzeitumgebung sichtbar sind", als eine einzelne Zahl oder "Weltalter" zu beschreiben. Es ermöglicht auch den Vergleich der in zwei Welten verfügbaren Methoden, indem einfach ihre ordinale Zahl verglichen wird. Im obigen Beispiel sehen wir, dass die "aktuelle Welt" (in der die Methode `newfun` existiert) um eins größer ist als die aufgabenlokale "Laufzeitwelt", die festgelegt wurde, als die Ausführung von `tryeval` begann.

Manchmal ist es notwendig, dies zu umgehen (zum Beispiel, wenn Sie das oben genannte REPL implementieren). Glücklicherweise gibt es eine einfache Lösung: Rufen Sie die Funktion mit [`Base.invokelatest`](@ref) auf:

```jldoctest
julia> function tryeval2()
           @eval newfun2() = 2
           Base.invokelatest(newfun2)
       end
tryeval2 (generic function with 1 method)

julia> tryeval2()
2
```

Schließlich wollen wir uns einige komplexere Beispiele ansehen, in denen diese Regel zur Anwendung kommt. Definieren Sie eine Funktion `f(x)`, die zunächst eine Methode hat:

```jldoctest redefinemethod
julia> f(x) = "original definition"
f (generic function with 1 method)
```

Beginnen Sie mit einigen anderen Operationen, die `f(x)` verwenden:

```jldoctest redefinemethod
julia> g(x) = f(x)
g (generic function with 1 method)

julia> t = @async f(wait()); yield();
```

Jetzt fügen wir einige neue Methoden zu `f(x)` hinzu:

```jldoctest redefinemethod
julia> f(x::Int) = "definition for Int"
f (generic function with 2 methods)

julia> f(x::Type{Int}) = "definition for Type{Int}"
f (generic function with 3 methods)
```

Vergleichen Sie, wie sich diese Ergebnisse unterscheiden:

```jldoctest redefinemethod
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> fetch(schedule(t, 1))
"original definition"

julia> t = @async f(wait()); yield();

julia> fetch(schedule(t, 1))
"definition for Int"
```

## Design Patterns with Parametric Methods

Während komplexe Dispatch-Logik für Leistung oder Benutzerfreundlichkeit nicht erforderlich ist, kann sie manchmal der beste Weg sein, um einen Algorithmus auszudrücken. Hier sind einige gängige Entwurfsmuster, die manchmal beim Einsatz von Dispatch in dieser Weise auftreten.

### Extracting the type parameter from a super-type

Hier ist eine korrekte Codevorlage für die Rückgabe des Elementtyps `T` eines beliebigen Untertyps von `AbstractArray`, der einen gut definierten Elementtyp hat:

```julia
abstract type AbstractArray{T, N} end
eltype(::Type{<:AbstractArray{T}}) where {T} = T
```

unter Verwendung der sogenannten dreieckigen Dispatch. Beachten Sie, dass `UnionAll`-Typen, wie zum Beispiel `eltype(AbstractArray{T} where T <: Integer)`, nicht mit der oben genannten Methode übereinstimmen. Die Implementierung von `eltype` in `Base` fügt in solchen Fällen eine Fallback-Methode für `Any` hinzu.

Ein häufiger Fehler besteht darin, zu versuchen, den Elementtyp durch Introspektion zu ermitteln:

```julia
eltype_wrong(::Type{A}) where {A<:AbstractArray} = A.parameters[1]
```

Es ist jedoch nicht schwer, Fälle zu konstruieren, in denen dies fehlschlägt:

```julia
struct BitVector <: AbstractArray{Bool, 1}; end
```

Hier haben wir einen Typ `BitVector` erstellt, der keine Parameter hat, bei dem jedoch der Elementtyp vollständig angegeben ist, wobei `T` gleich `Bool` ist!

Ein weiterer Fehler besteht darin, zu versuchen, die Typ-Hierarchie mit `supertype` zu durchlaufen:

```julia
eltype_wrong(::Type{AbstractArray{T}}) where {T} = T
eltype_wrong(::Type{AbstractArray{T, N}}) where {T, N} = T
eltype_wrong(::Type{A}) where {A<:AbstractArray} = eltype_wrong(supertype(A))
```

Während dies für deklarierte Typen funktioniert, schlägt es bei Typen ohne Supertypen fehl:

```julia-repl
julia> eltype_wrong(Union{AbstractArray{Int}, AbstractArray{Float64}})
ERROR: MethodError: no method matching supertype(::Type{Union{AbstractArray{Float64,N} where N, AbstractArray{Int64,N} where N}})
Closest candidates are:
  supertype(::DataType) at operators.jl:43
  supertype(::UnionAll) at operators.jl:48
```

### Building a similar type with a different type parameter

Beim Erstellen von generischem Code besteht häufig die Notwendigkeit, ein ähnliches Objekt mit einer Änderung des Layouts des Typs zu konstruieren, was auch eine Änderung der Typparameter erfordert. Zum Beispiel könnten Sie eine Art abstraktes Array mit einem beliebigen Elementtyp haben und Ihre Berechnung darauf mit einem spezifischen Elementtyp durchführen wollen. Wir müssen eine Methode für jede `AbstractArray{T}`-Unterklasse implementieren, die beschreibt, wie dieser Typtransformationsprozess durchgeführt wird. Es gibt keine allgemeine Transformation von einer Unterklasse in eine andere Unterklasse mit einem anderen Parameter.

Die Subtypen von `AbstractArray` implementieren typischerweise zwei Methoden, um dies zu erreichen: Eine Methode, um das Eingabearray in einen Subtyp eines bestimmten `AbstractArray{T, N}`-Abstrakttyps zu konvertieren; und eine Methode, um ein neues, uninitialisiertes Array mit einem bestimmten Elementtyp zu erstellen. Beispielimplementierungen davon sind in Julia Base zu finden. Hier ist ein grundlegendes Beispiel für die Verwendung dieser Methoden, das garantiert, dass `input` und `output` vom gleichen Typ sind:

```julia
input = convert(AbstractArray{Eltype}, input)
output = similar(input, Eltype)
```

Als Erweiterung davon ist in Fällen, in denen der Algorithmus eine Kopie des Eingabearrays benötigt, [`convert`](@ref) unzureichend, da der Rückgabewert möglicherweise mit dem ursprünglichen Eingabewert aliasiert. Die Kombination von [`similar`](@ref) (um das Ausgabearray zu erstellen) und [`copyto!`](@ref) (um es mit den Eingabedaten zu füllen) ist eine allgemeine Möglichkeit, die Anforderung für eine veränderbare Kopie des Eingabearguments auszudrücken:

```julia
copy_with_eltype(input, Eltype) = copyto!(similar(input, Eltype), input)
```

### Iterated dispatch

Um eine mehrstufige parametrische Argumentliste zu versenden, ist es oft am besten, jede Stufe des Dispatch in separate Funktionen zu unterteilen. Dies mag im Ansatz dem Single-Dispatch ähnlich klingen, aber wie wir gleich sehen werden, ist es dennoch flexibler.

Zum Beispiel wird der Versuch, auf den Elementtyp eines Arrays zu dispatchen, oft auf mehrdeutige Situationen stoßen. Stattdessen wird in der Regel zuerst auf den Containertyp dispatcht, dann wird rekursiv zu einer spezifischeren Methode basierend auf eltype weitergegangen. In den meisten Fällen eignen sich die Algorithmen bequem für diesen hierarchischen Ansatz, während in anderen Fällen diese Strenge manuell gelöst werden muss. Diese Dispatch-Zweigung kann beispielsweise in der Logik zum Summieren von zwei Matrizen beobachtet werden:

```julia
# First dispatch selects the map algorithm for element-wise summation.
+(a::Matrix, b::Matrix) = map(+, a, b)
# Then dispatch handles each element and selects the appropriate
# common element type for the computation.
+(a, b) = +(promote(a, b)...)
# Once the elements have the same type, they can be added.
# For example, via primitive operations exposed by the processor.
+(a::Float64, b::Float64) = Core.add(a, b)
```

### Trait-based dispatch

Eine natürliche Erweiterung des oben beschriebenen iterierten Dispatchs besteht darin, eine Schicht zur Methodenauswahl hinzuzufügen, die es ermöglicht, auf Mengen von Typen zu dispatchen, die unabhängig von den durch die Typ-Hierarchie definierten Mengen sind. Wir könnten eine solche Menge konstruieren, indem wir eine `Union` der betreffenden Typen aufschreiben, aber dann wäre diese Menge nicht erweiterbar, da `Union`-Typen nach ihrer Erstellung nicht mehr verändert werden können. Eine solche erweiterbare Menge kann jedoch mit einem Entwurfsmuster programmiert werden, das oft als ["Holy-trait"](https://github.com/JuliaLang/julia/issues/2345#issuecomment-54537633) bezeichnet wird.

Dieses Muster wird implementiert, indem eine generische Funktion definiert wird, die für jede Trait-Menge, zu der die Funktionsargumente gehören können, einen anderen Singleton-Wert (oder -typ) berechnet. Wenn diese Funktion rein ist, hat sie im Vergleich zu normalem Dispatch keinen Einfluss auf die Leistung.

Das Beispiel im vorherigen Abschnitt hat die Implementierungsdetails von [`map`](@ref) und [`promote`](@ref) übergangen, die beide in Bezug auf diese Eigenschaften arbeiten. Bei der Iteration über eine Matrix, wie in der Implementierung von `map`, ist eine wichtige Frage, welche Reihenfolge verwendet werden soll, um die Daten zu durchlaufen. Wenn `AbstractArray`-Subtypen das [`Base.IndexStyle`](@ref)-Trait implementieren, können andere Funktionen wie `map` auf diese Informationen zugreifen, um den besten Algorithmus auszuwählen (siehe [Abstract Array Interface](@ref man-interface-array)). Das bedeutet, dass jeder Subtyp keine benutzerdefinierte Version von `map` implementieren muss, da die generischen Definitionen + Trait-Klassen es dem System ermöglichen, die schnellste Version auszuwählen. Hier ist eine Spielzeugimplementierung von `map`, die die trait-basierte Dispatch zeigt:

```julia
map(f, a::AbstractArray, b::AbstractArray) = map(Base.IndexStyle(a, b), f, a, b)
# generic implementation:
map(::Base.IndexCartesian, f, a::AbstractArray, b::AbstractArray) = ...
# linear-indexing implementation (faster)
map(::Base.IndexLinear, f, a::AbstractArray, b::AbstractArray) = ...
```

Dieser eigenschaftsbasierte Ansatz ist auch im [`promote`](@ref) Mechanismus vorhanden, der von dem Skalar `+` verwendet wird. Er nutzt [`promote_type`](@ref), das den optimalen gemeinsamen Typ zurückgibt, um die Operation unter Berücksichtigung der beiden Typen der Operanden zu berechnen. Dies ermöglicht es, das Problem der Implementierung jeder Funktion für jedes mögliche Typenpaar auf das viel kleinere Problem zu reduzieren, eine Umwandlungsoperation von jedem Typ in einen gemeinsamen Typ zu implementieren, plus eine Tabelle bevorzugter paarweiser Aufwertungsregeln.

### Output-type computation

Die Diskussion über die eigenschaftsbasierte Förderung bietet einen Übergang zu unserem nächsten Entwurfsmuster: die Berechnung des Ausgabeelementtyps für eine Matrixoperation.

Für die Implementierung primitiver Operationen, wie z.B. Addition, verwenden wir die [`promote_type`](@ref)-Funktion, um den gewünschten Ausgabetyp zu berechnen. (Wie zuvor haben wir dies bei der `promote`-Aufruf in dem Aufruf von `+` gesehen).

Für komplexere Funktionen auf Matrizen kann es notwendig sein, den erwarteten Rückgabetyp für eine komplexere Folge von Operationen zu berechnen. Dies wird oft durch die folgenden Schritte durchgeführt:

1. Write a small function `op` that expresses the set of operations performed by the kernel of the algorithm.
2. Berechne den Elementtyp `R` der Ergebnismatrix als `promote_op(op, argument_types...)`, wobei `argument_types` aus `eltype` abgeleitet wird, das auf jedes Eingabearray angewendet wird.
3. Erstellen Sie die Ausgabematrix als `similar(R, dims)`, wobei `dims` die gewünschten Dimensionen des Ausgabearrays sind.

Für ein spezifischeres Beispiel könnte ein generischer Pseudo-Code für die Multiplikation von Quadratmatrizen folgendermaßen aussehen:

```julia
function matmul(a::AbstractMatrix, b::AbstractMatrix)
    op = (ai, bi) -> ai * bi + ai * bi

    ## this is insufficient because it assumes `one(eltype(a))` is constructable:
    # R = typeof(op(one(eltype(a)), one(eltype(b))))

    ## this fails because it assumes `a[1]` exists and is representative of all elements of the array
    # R = typeof(op(a[1], b[1]))

    ## this is incorrect because it assumes that `+` calls `promote_type`
    ## but this is not true for some types, such as Bool:
    # R = promote_type(ai, bi)

    # this is wrong, since depending on the return value
    # of type-inference is very brittle (as well as not being optimizable):
    # R = Base.return_types(op, (eltype(a), eltype(b)))

    ## but, finally, this works:
    R = promote_op(op, eltype(a), eltype(b))
    ## although sometimes it may give a larger type than desired
    ## it will always give a correct type

    output = similar(b, R, (size(a, 1), size(b, 2)))
    if size(a, 2) > 0
        for j in 1:size(b, 2)
            for i in 1:size(a, 1)
                ## here we don't use `ab = zero(R)`,
                ## since `R` might be `Any` and `zero(Any)` is not defined
                ## we also must declare `ab::R` to make the type of `ab` constant in the loop,
                ## since it is possible that typeof(a * b) != typeof(a * b + a * b) == R
                ab::R = a[i, 1] * b[1, j]
                for k in 2:size(a, 2)
                    ab += a[i, k] * b[k, j]
                end
                output[i, j] = ab
            end
        end
    end
    return output
end
```

### Separate convert and kernel logic

Eine Möglichkeit, die Kompilierzeiten und die Komplexität der Tests erheblich zu reduzieren, besteht darin, die Logik für die Umwandlung in den gewünschten Typ und die Berechnung zu isolieren. Dies ermöglicht es dem Compiler, die Umwandlungslogik unabhängig vom Rest des Körpers des größeren Kerns zu spezialisieren und inline zu setzen.

Dies ist ein häufiges Muster, das beim Konvertieren von einer größeren Klasse von Typen zu dem spezifischen Argumenttyp, der tatsächlich von dem Algorithmus unterstützt wird, zu sehen ist:

```julia
complexfunction(arg::Int) = ...
complexfunction(arg::Any) = complexfunction(convert(Int, arg))

matmul(a::T, b::T) = ...
matmul(a, b) = matmul(promote(a, b)...)
```

## Parametrically-constrained Varargs methods

Funktionsparameter können auch verwendet werden, um die Anzahl der Argumente einzuschränken, die an eine "varargs"-Funktion ([Varargs Functions](@ref)) übergeben werden dürfen. Die Notation `Vararg{T,N}` wird verwendet, um eine solche Einschränkung anzuzeigen. Zum Beispiel:

```jldoctest
julia> bar(a,b,x::Vararg{Any,2}) = (a,b,x)
bar (generic function with 1 method)

julia> bar(1,2,3)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, !Matched::Any)
   @ Main none:1

Stacktrace:
[...]

julia> bar(1,2,3,4)
(1, 2, (3, 4))

julia> bar(1,2,3,4,5)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

Nützlicherweise ist es möglich, varargs-Methoden durch einen Parameter einzuschränken. Zum Beispiel:

```julia
function getindex(A::AbstractArray{T,N}, indices::Vararg{Number,N}) where {T,N}
```

wird nur aufgerufen, wenn die Anzahl der `indices` mit der Dimensionalität des Arrays übereinstimmt.

Wenn nur der Typ der übergebenen Argumente eingeschränkt werden muss, kann `Vararg{T}` gleichwertig als `T...` geschrieben werden. Zum Beispiel ist `f(x::Int...) = x` eine Kurzform für `f(x::Vararg{Int}) = x`.

## Note on Optional and keyword Arguments

Wie kurz in [Functions](@ref man-functions) erwähnt, werden optionale Argumente als Syntax für mehrere Methodendefinitionen implementiert. Zum Beispiel diese Definition:

```julia
f(a=1,b=2) = a+2b
```

übersetzt in die folgenden drei Methoden:

```julia
f(a,b) = a+2b
f(a) = f(a,2)
f() = f(1,2)
```

Das bedeutet, dass der Aufruf von `f()` dem Aufruf von `f(1,2)` entspricht. In diesem Fall ist das Ergebnis `5`, da `f(1,2)` die erste Methode von `f` oben aufruft. Dies muss jedoch nicht immer der Fall sein. Wenn Sie eine vierte Methode definieren, die spezialisierter für Ganzzahlen ist:

```julia
f(a::Int,b::Int) = a-2b
```

Dann ist das Ergebnis sowohl von `f()` als auch von `f(1,2)` `-3`. Mit anderen Worten, optionale Argumente sind an eine Funktion gebunden, nicht an eine spezifische Methode dieser Funktion. Es hängt von den Typen der optionalen Argumente ab, welche Methode aufgerufen wird. Wenn optionale Argumente in Bezug auf eine globale Variable definiert sind, kann sich der Typ des optionalen Arguments sogar zur Laufzeit ändern.

Schlüsselwortargumente verhalten sich ganz anders als gewöhnliche Positionsargumente. Insbesondere nehmen sie nicht an der Methodenaufrufverarbeitung teil. Methoden werden ausschließlich basierend auf Positionsargumenten aufgerufen, wobei Schlüsselwortargumente verarbeitet werden, nachdem die passende Methode identifiziert wurde.

## Function-like objects

Methoden sind mit Typen verbunden, sodass es möglich ist, jedes beliebige Julia-Objekt "aufrufbar" zu machen, indem man Methoden zu seinem Typ hinzufügt. (Solche "aufrufbaren" Objekte werden manchmal "Funktoren" genannt.)

Zum Beispiel können Sie einen Typ definieren, der die Koeffizienten eines Polynoms speichert, sich jedoch wie eine Funktion verhält, die das Polynom auswertet:

```jldoctest polynomial
julia> struct Polynomial{R}
           coeffs::Vector{R}
       end

julia> function (p::Polynomial)(x)
           v = p.coeffs[end]
           for i = (length(p.coeffs)-1):-1:1
               v = v*x + p.coeffs[i]
           end
           return v
       end

julia> (p::Polynomial)() = p(5)
```

Beachten Sie, dass die Funktion durch den Typ und nicht durch den Namen spezifiziert ist. Wie bei normalen Funktionen gibt es eine knappe Syntaxform. Im Funktionskörper wird `p` auf das Objekt verweisen, das aufgerufen wurde. Ein `Polynomial` kann wie folgt verwendet werden:

```jldoctest polynomial
julia> p = Polynomial([1,10,100])
Polynomial{Int64}([1, 10, 100])

julia> p(3)
931

julia> p()
2551
```

Dieser Mechanismus ist auch der Schlüssel dafür, wie Typkonstruktoren und Closures (innere Funktionen, die auf ihre umgebende Umgebung verweisen) in Julia funktionieren.

## Empty generic functions

Gelegentlich ist es nützlich, eine generische Funktion einzuführen, ohne bereits Methoden hinzuzufügen. Dies kann verwendet werden, um Schnittstellendefinitionen von Implementierungen zu trennen. Es kann auch aus Gründen der Dokumentation oder der Lesbarkeit des Codes erfolgen. Die Syntax dafür ist ein leerer `function`-Block ohne ein Tupel von Argumenten:

```julia
function emptyfunc end
```

## [Method design and the avoidance of ambiguities](@id man-method-design-ambiguities)

Julias Methoden-Polymorphismus ist eines seiner mächtigsten Merkmale, doch die Ausnutzung dieser Kraft kann Designherausforderungen mit sich bringen. Insbesondere in komplexeren Methodenhierarchien ist es nicht ungewöhnlich, dass [ambiguities](@ref man-ambiguities) auftaucht.

Oben wurde darauf hingewiesen, dass man Mehrdeutigkeiten wie lösen kann

```julia
f(x, y::Int) = 1
f(x::Int, y) = 2
```

durch die Definition einer Methode

```julia
f(x::Int, y::Int) = 3
```

Dies ist oft die richtige Strategie; jedoch gibt es Umstände, in denen das gedankenlose Befolgen dieses Ratschlags kontraproduktiv sein kann. Insbesondere je mehr Methoden eine generische Funktion hat, desto mehr Möglichkeiten gibt es für Mehrdeutigkeiten. Wenn Ihre Methodenhierarchien komplizierter werden als dieses einfache Beispiel, kann es sich lohnen, sorgfältig über alternative Strategien nachzudenken.

Im Folgenden erörtern wir bestimmte Herausforderungen und einige alternative Möglichkeiten, solche Probleme zu lösen.

### Tuple and NTuple arguments

`Tuple` (und `NTuple`) Argumente stellen besondere Herausforderungen dar. Zum Beispiel,

```julia
f(x::NTuple{N,Int}) where {N} = 1
f(x::NTuple{N,Float64}) where {N} = 2
```

sind mehrdeutig aufgrund der Möglichkeit, dass `N == 0` ist: Es gibt keine Elemente, um zu bestimmen, ob die `Int`- oder `Float64`-Variante aufgerufen werden sollte. Um die Mehrdeutigkeit zu lösen, besteht ein Ansatz darin, eine Methode für das leere Tupel zu definieren:

```julia
f(x::Tuple{}) = 3
```

Alternativ können Sie für alle Methoden mit Ausnahme einer darauf bestehen, dass es mindestens ein Element im Tupel gibt:

```julia
f(x::NTuple{N,Int}) where {N} = 1           # this is the fallback
f(x::Tuple{Float64, Vararg{Float64}}) = 2   # this requires at least one Float64
```

### [Orthogonalize your design](@id man-methods-orthogonalize)

Wenn Sie versucht sind, mit zwei oder mehr Argumenten zu arbeiten, überlegen Sie, ob eine "Wrapper"-Funktion für ein einfacheres Design sorgen könnte. Anstatt mehrere Varianten zu schreiben:

```julia
f(x::A, y::A) = ...
f(x::A, y::B) = ...
f(x::B, y::A) = ...
f(x::B, y::B) = ...
```

du könntest in Betracht ziehen, zu definieren

```julia
f(x::A, y::A) = ...
f(x, y) = f(g(x), g(y))
```

wo `g` das Argument in den Typ `A` umwandelt. Dies ist ein sehr spezifisches Beispiel für das allgemeinere Prinzip von [orthogonal design](https://en.wikipedia.org/wiki/Orthogonality_(programming)), bei dem separate Konzepte separaten Methoden zugewiesen werden. Hier wird `g` höchstwahrscheinlich eine Fallback-Definition benötigen.

```julia
g(x::A) = x
```

Eine verwandte Strategie nutzt `promote`, um `x` und `y` in einen gemeinsamen Typ zu bringen:

```julia
f(x::T, y::T) where {T} = ...
f(x, y) = f(promote(x, y)...)
```

Ein Risiko bei diesem Design ist die Möglichkeit, dass, wenn es keine geeignete Promotionsmethode gibt, um `x` und `y` in denselben Typ zu konvertieren, die zweite Methode sich unendlich rekursiv aufruft und einen Stacküberlauf auslöst.

### Dispatch on one argument at a time

Wenn Sie auf mehrere Argumente dispatchen müssen und es viele Fallbacks mit zu vielen Kombinationen gibt, um alle möglichen Varianten praktisch zu definieren, sollten Sie in Betracht ziehen, eine "Namens-Kaskade" einzuführen, bei der (zum Beispiel) auf das erste Argument dispatchen und dann eine interne Methode aufrufen:

```julia
f(x::A, y) = _fA(x, y)
f(x::B, y) = _fB(x, y)
```

Dann können die internen Methoden `_fA` und `_fB` auf `y` dispatchen, ohne sich um Mehrdeutigkeiten miteinander in Bezug auf `x` sorgen zu müssen.

Seien Sie sich bewusst, dass diese Strategie mindestens einen wesentlichen Nachteil hat: In vielen Fällen ist es für Benutzer nicht möglich, das Verhalten von `f` weiter anzupassen, indem sie weitere Spezialisierungen Ihrer exportierten Funktion `f` definieren. Stattdessen müssen sie Spezialisierungen für Ihre internen Methoden `_fA` und `_fB` definieren, und dies verwischt die Grenzen zwischen exportierten und internen Methoden.

### Abstract containers and element types

Wo möglich, versuchen Sie, Methoden zu vermeiden, die auf spezifische Elementtypen von abstrakten Containern dispatchen. Zum Beispiel,

```julia
-(A::AbstractArray{T}, b::Date) where {T<:Date}
```

generiert Mehrdeutigkeiten für jeden, der eine Methode definiert

```julia
-(A::MyArrayType{T}, b::T) where {T}
```

Der beste Ansatz ist, *keine* dieser Methoden zu definieren: Stattdessen sollten Sie sich auf eine generische Methode `-(A::AbstractArray, b)` verlassen und sicherstellen, dass diese Methode mit generischen Aufrufen (wie `similar` und `-`) implementiert wird, die für jeden Containertyp und jeden Elementtyp *separat* das Richtige tun. Dies ist nur eine komplexere Variante des Ratschlags, Ihre Methoden zu [orthogonalize](@ref man-methods-orthogonalize) zu gestalten.

Wenn dieser Ansatz nicht möglich ist, kann es sinnvoll sein, eine Diskussion mit anderen Entwicklern über die Klärung der Mehrdeutigkeit zu beginnen; nur weil eine Methode zuerst definiert wurde, bedeutet das nicht unbedingt, dass sie nicht geändert oder eliminiert werden kann. Als letzte Möglichkeit kann ein Entwickler die "Überbrückungsmethode" definieren.

```julia
-(A::MyArrayType{T}, b::Date) where {T<:Date} = ...
```

das die Mehrdeutigkeit mit roher Gewalt löst.

### Complex method "cascades" with default arguments

Wenn Sie eine Methode "cascade" definieren, die Standardwerte bereitstellt, seien Sie vorsichtig, keine Argumente wegzulassen, die potenziellen Standardwerten entsprechen. Angenommen, Sie schreiben einen digitalen Filteralgorithmus und haben eine Methode, die die Ränder des Signals behandelt, indem sie Padding anwendet:

```julia
function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel)  # now perform the "real" computation
end
```

Dies wird gegen eine Methode verstoßen, die standardmäßige Polsterung bereitstellt:

```julia
myfilter(A, kernel) = myfilter(A, kernel, Replicate()) # replicate the edge by default
```

Zusammen erzeugen diese beiden Methoden eine unendliche Rekursion, bei der `A` ständig größer wird.

Das bessere Design wäre, Ihre Aufrufhierarchie wie folgt zu definieren:

```julia
struct NoPad end  # indicate that no padding is desired, or that it's already applied

myfilter(A, kernel) = myfilter(A, kernel, Replicate())  # default boundary conditions

function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel, NoPad())  # indicate the new boundary conditions
end

# other padding methods go here

function myfilter(A, kernel, ::NoPad)
    # Here's the "real" implementation of the core computation
end
```

`NoPad` wird in derselben Argumentposition wie jede andere Art von Padding bereitgestellt, sodass die Dispatch-Hierarchie gut organisiert bleibt und die Wahrscheinlichkeit von Mehrdeutigkeiten verringert wird. Darüber hinaus erweitert es die "öffentliche" `myfilter`-Schnittstelle: Ein Benutzer, der das Padding explizit steuern möchte, kann die `NoPad`-Variante direkt aufrufen.

## Defining methods in local scope

Sie können Methoden innerhalb eines [local scope](@ref scope-of-variables) definieren, zum Beispiel

```jldoctest
julia> function f(x)
           g(y::Int) = y + x
           g(y) = y - x
           g
       end
f (generic function with 1 method)

julia> h = f(3);

julia> h(4)
7

julia> h(4.0)
1.0
```

Sie sollten jedoch *keine* lokalen Methoden bedingt oder unter Kontrolle des Flusses definieren, wie in

```julia
function f2(inc)
    if inc
        g(x) = x + 1
    else
        g(x) = x - 1
    end
end

function f3()
    function g end
    return g
    g() = 0
end
```

da es unklar ist, welche Funktion letztendlich definiert wird. In Zukunft könnte es ein Fehler sein, lokale Methoden auf diese Weise zu definieren.

Für solche Fälle verwenden Sie stattdessen anonyme Funktionen:

```julia
function f2(inc)
    g = if inc
        x -> x + 1
    else
        x -> x - 1
    end
end
```

[^Clarke61]: Arthur C. Clarke, *Profiles of the Future* (1961): Clarke's Third Law.
