# Base.Cartesian

Das (nicht exportierte) Cartesian-Modul bietet Makros, die das Schreiben von multidimensionalen Algorithmen erleichtern. Am häufigsten können Sie solche Algorithmen mit [straightforward techniques](https://julialang.org/blog/2016/02/iteration) schreiben; es gibt jedoch einige Fälle, in denen `Base.Cartesian` immer noch nützlich oder notwendig ist.

## Principles of usage

Ein einfaches Beispiel für die Verwendung ist:

```julia
@nloops 3 i A begin
    s += @nref 3 A i
end
```

welches den folgenden Code generiert:

```julia
for i_3 = axes(A, 3)
    for i_2 = axes(A, 2)
        for i_1 = axes(A, 1)
            s += A[i_1, i_2, i_3]
        end
    end
end
```

Im Allgemeinen ermöglicht es Cartesian, generischen Code zu schreiben, der sich wiederholende Elemente enthält, wie die geschachtelten Schleifen in diesem Beispiel. Weitere Anwendungen umfassen wiederholte Ausdrücke (z. B. Schleifenentfaltung) oder das Erstellen von Funktionsaufrufen mit variablen Argumentanzahlen, ohne die "Splat"-Konstruktion (`i...`) zu verwenden.

## Basic syntax

Die (grundlegende) Syntax von `@nloops` ist wie folgt:

  * Das erste Argument muss eine Ganzzahl (*keine* Variable) sein, die die Anzahl der Schleifen angibt.
  * Das zweite Argument ist das Symbol-Präfix, das für die Iterator-Variable verwendet wird. Hier haben wir `i` verwendet, und die Variablen `i_1, i_2, i_3` wurden generiert.
  * Das dritte Argument gibt den Bereich für jede Iterator-Variable an. Wenn Sie hier eine Variable (Symbol) verwenden, wird sie als `axes(A, dim)` interpretiert. Flexibler können Sie die unten beschriebene Syntax für anonyme Funktionsausdrücke verwenden.
  * Das letzte Argument ist der Körper der Schleife. Hier ist das, was zwischen `begin...end` erscheint.

Es gibt einige zusätzliche Funktionen von `@nloops`, die in der [reference section](@ref dev-cartesian-reference) beschrieben sind.

`@nref` folgt einem ähnlichen Muster und erzeugt `A[i_1,i_2,i_3]` aus `@nref 3 A i`. Die allgemeine Praxis besteht darin, von links nach rechts zu lesen, weshalb `@nloops` `@nloops 3 i A expr` ist (wie in `for i_2 = axes(A, 2)`, wobei `i_2` links steht und der Bereich rechts steht), während `@nref` `@nref 3 A i` ist (wie in `A[i_1,i_2,i_3]`, wobei das Array zuerst kommt).

Wenn Sie Code mit Cartesian entwickeln, stellen Sie möglicherweise fest, dass das Debuggen einfacher ist, wenn Sie den generierten Code mit `@macroexpand` untersuchen:

```@meta
DocTestSetup = quote
    import Base.Cartesian: @nref
end
```

```jldoctest
julia> @macroexpand @nref 2 A i
:(A[i_1, i_2])
```

```@meta
DocTestSetup = nothing
```

### Supplying the number of expressions

Das erste Argument beider dieser Makros ist die Anzahl der Ausdrücke, die eine ganze Zahl sein muss. Wenn Sie eine Funktion schreiben, die in mehreren Dimensionen funktionieren soll, möchten Sie dies möglicherweise nicht fest codieren. Der empfohlene Ansatz ist die Verwendung einer `@generated function`. Hier ist ein Beispiel:

```julia
@generated function mysum(A::Array{T,N}) where {T,N}
    quote
        s = zero(T)
        @nloops $N i A begin
            s += @nref $N A i
        end
        s
    end
end
```

Natürlich können Sie auch Ausdrücke vorbereiten oder Berechnungen vor dem `quote`-Block durchführen.

### Anonymous-function expressions as macro arguments

Vielleicht ist das einzige, aber mächtigste Merkmal von `Cartesian` die Möglichkeit, anonyme Funktionsausdrücke bereitzustellen, die zur Parsing-Zeit ausgewertet werden. Lassen Sie uns ein einfaches Beispiel betrachten:

```julia
@nexprs 2 j->(i_j = 1)
```

`@nexprs` generiert `n` Ausdrücke, die einem Muster folgen. Dieser Code würde die folgenden Aussagen erzeugen:

```julia
i_1 = 1
i_2 = 1
```

In jeder generierten Aussage wird ein "isoliertes" `j` (die Variable der anonymen Funktion) durch Werte im Bereich `1:2` ersetzt. Allgemein verwendet Cartesian eine LaTeX-ähnliche Syntax. Dies ermöglicht es Ihnen, mathematische Operationen auf dem Index `j` durchzuführen. Hier ist ein Beispiel zur Berechnung der Schritte eines Arrays:

```julia
s_1 = 1
@nexprs 3 j->(s_{j+1} = s_j * size(A, j))
```

würde Ausdrücke generieren

```julia
s_1 = 1
s_2 = s_1 * size(A, 1)
s_3 = s_2 * size(A, 2)
s_4 = s_3 * size(A, 3)
```

Anonyme Funktionsausdrücke haben in der Praxis viele Anwendungen.

#### [Macro reference](@id dev-cartesian-reference)

```@docs
Base.Cartesian.@nloops
Base.Cartesian.@nref
Base.Cartesian.@nextract
Base.Cartesian.@nexprs
Base.Cartesian.@ncall
Base.Cartesian.@ncallkw
Base.Cartesian.@ntuple
Base.Cartesian.@nall
Base.Cartesian.@nany
Base.Cartesian.@nif
```
