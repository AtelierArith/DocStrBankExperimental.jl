# Reflection and introspection

Julia bietet eine Vielzahl von Laufzeit-Reflexionsfähigkeiten.

## Module bindings

Die öffentlichen Namen für ein `Module` sind verfügbar über [`names(m::Module)`](@ref), was ein Array von [`Symbol`](@ref) Elementen zurückgibt, die die öffentlichen Bindungen darstellen. `names(m::Module, all = true)` gibt Symbole für alle Bindungen in `m` zurück, unabhängig vom öffentlichen Status.

## DataType fields

Die Namen der `DataType`-Felder können mit [`fieldnames`](@ref) abgefragt werden. Zum Beispiel gibt der folgende Typ `fieldnames(Point)` ein Tupel von [`Symbol`](@ref)s zurück, die die Feldnamen darstellen:

```jldoctest struct_point
julia> struct Point
           x::Int
           y
       end

julia> fieldnames(Point)
(:x, :y)
```

Der Typ jedes Feldes in einem `Point`-Objekt wird im `types`-Feld der `Point`-Variablen selbst gespeichert:

```jldoctest struct_point
julia> Point.types
svec(Int64, Any)
```

Während `x` als `Int` annotiert ist, wurde `y` in der Typdefinition nicht annotiert, daher wird `y` standardmäßig vom Typ `Any`.

Typen werden selbst als eine Struktur namens `DataType` dargestellt:

```jldoctest struct_point
julia> typeof(Point)
DataType
```

Beachten Sie, dass `fieldnames(DataType)` die Namen für jedes Feld von `DataType` selbst zurückgibt, und eines dieser Felder ist das `types`-Feld, das im obigen Beispiel beobachtet wurde.

## Subtypes

Die *direkten* Subtypen eines beliebigen `DataType` können mit [`subtypes`](@ref) aufgelistet werden. Zum Beispiel hat der abstrakte `DataType` [`AbstractFloat`](@ref) vier (konkrete) Subtypen:

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.subtypes(AbstractFloat)
5-element Vector{Any}:
 BigFloat
 Core.BFloat16
 Float16
 Float32
 Float64
```

Jeder abstrakte Subtyp wird ebenfalls in dieser Liste enthalten sein, aber weitere Subtypen davon nicht; die rekursive Anwendung von [`subtypes`](@ref) kann verwendet werden, um den vollständigen Typbaum zu inspizieren.

Beachten Sie, dass [`subtypes`](@ref) sich innerhalb von [`InteractiveUtils`](@ref man-interactive-utils) befindet, aber automatisch exportiert wird, wenn das REPL verwendet wird.

## DataType layout

Die interne Darstellung eines `DataType` ist entscheidend, wenn man mit C-Code interagiert, und mehrere Funktionen stehen zur Verfügung, um diese Details zu inspizieren. [`isbitstype(T::DataType)`](@ref) gibt true zurück, wenn `T` mit C-kompatibler Ausrichtung gespeichert ist. [`fieldoffset(T::DataType, i::Integer)`](@ref) gibt den (Byte-)Offset für das Feld *i* relativ zum Beginn des Typs zurück.

## Function methods

Die Methoden einer beliebigen Funktion können mit [`methods`](@ref) aufgelistet werden. Die Methodenzuordnungstabelle kann nach Methoden durchsucht werden, die einen bestimmten Typ akzeptieren, mit [`methodswith`](@ref).

## Expansion and lowering

Wie im Abschnitt [Metaprogramming](@ref) besprochen, gibt die Funktion [`macroexpand`](@ref) den unquoted und interpolierten Ausdruck ([`Expr`](@ref)) für ein gegebenes Makro zurück. Um `macroexpand` zu verwenden, muss der Ausdrucksblock selbst `quote`-iert werden (ansonsten wird das Makro ausgewertet und das Ergebnis wird stattdessen übergeben!). Zum Beispiel:

```jldoctest; setup = :(using InteractiveUtils)
julia> InteractiveUtils.macroexpand(@__MODULE__, :(@edit println("")) )
:(InteractiveUtils.edit(println, (Base.typesof)("")))
```

Die Funktionen `Base.Meta.show_sexpr` und [`dump`](@ref) werden verwendet, um S-expr-Stilansichten und tief verschachtelte Detailansichten für beliebige Ausdrücke anzuzeigen.

Schließlich gibt die [`Meta.lower`](@ref)-Funktion die `lowered`-Form eines beliebigen Ausdrucks zurück und ist von besonderem Interesse, um zu verstehen, wie Sprachkonstrukte auf primitive Operationen wie Zuweisungen, Verzweigungen und Aufrufe abgebildet werden:

```jldoctest; setup = (using Base: +, sin)
julia> Meta.lower(@__MODULE__, :( [1+2, sin(0.5)] ))
:($(Expr(:thunk, CodeInfo(
    @ none within `top-level scope`
1 ─ %1 = 1 + 2
│   %2 = sin(0.5)
│   %3 = Base.vect(%1, %2)
└──      return %3
))))
```

## Intermediate and compiled representations

Die Inspektion der gesenkten Form für Funktionen erfordert die Auswahl der spezifischen Methode zur Anzeige, da generische Funktionen viele Methoden mit unterschiedlichen Typ-Signaturen haben können. Zu diesem Zweck ist eine methodenspezifische Code-Senkung verfügbar, die mit [`code_lowered`](@ref) verwendet werden kann, und die typ-inferierte Form ist verfügbar mit [`code_typed`](@ref). [`code_warntype`](@ref) fügt der Ausgabe von `4d61726b646f776e2e436f64652822222c2022636f64655f74797065642229_40726566` Hervorhebungen hinzu.

Näher an der Maschine kann die LLVM-Zwischenrepräsentation einer Funktion mit [`code_llvm`](@ref) ausgegeben werden, und schließlich ist der kompilierte Maschinencode mit [`code_native`](@ref) verfügbar (dies löst die JIT-Kompilierung/code-Generierung für jede Funktion aus, die zuvor nicht aufgerufen wurde).

Zur Vereinfachung gibt es Makroversionen der oben genannten Funktionen, die Standardfunktionsaufrufe übernehmen und die Argumenttypen automatisch erweitern:

```julia-repl
julia> @code_llvm +(1,1)
;  @ int.jl:87 within `+`
; Function Attrs: sspstrong uwtable
define i64 @"julia_+_476"(i64 signext %0, i64 signext %1) #0 {
top:
  %2 = add i64 %1, %0
  ret i64 %2
}
```

Für weitere Informationen siehe [`@code_lowered`](@ref), [`@code_typed`](@ref), [`@code_warntype`](@ref), [`@code_llvm`](@ref), und [`@code_native`](@ref).

### Printing of debug information

Die oben genannten Funktionen und Makros nehmen das Schlüsselwortargument `debuginfo`, das das Niveau der ausgegebenen Debug-Informationen steuert.

```jldoctest; setup = :(using InteractiveUtils), filter = r"int.jl:\d+"
julia> InteractiveUtils.@code_typed debuginfo=:source +(1,1)
CodeInfo(
    @ int.jl:87 within `+`
1 ─ %1 = Base.add_int(x, y)::Int64
└──      return %1
) => Int64
```

Mögliche Werte für `debuginfo` sind: `:none`, `:source` und `:default`. Standardmäßig werden keine Debug-Informationen ausgegeben, dies kann jedoch geändert werden, indem `Base.IRShow.default_debuginfo[] = :source` gesetzt wird.
