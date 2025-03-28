```
@nospecialize
```

Angewendet auf einen Funktionsargumentnamen weist der Compiler darauf hin, dass die Implementierung der Methode nicht für verschiedene Typen dieses Arguments spezialisiert werden sollte, sondern stattdessen den deklarierten Typ für dieses Argument verwendet werden soll. Es kann auf ein Argument innerhalb einer formalen Argumentliste oder im Funktionskörper angewendet werden. Wenn es auf ein Argument angewendet wird, muss das Makro den gesamten Argumentausdruck umschließen, z. B. `@nospecialize(x::Real)` oder `@nospecialize(i::Integer...)`, anstatt nur den Argumentnamen zu umschließen. Wenn es im Funktionskörper verwendet wird, muss das Makro an einer Anweisungstelle und vor jeglichem Code auftreten.

Wenn es ohne Argumente verwendet wird, gilt es für alle Argumente des übergeordneten Bereichs. Im lokalen Bereich bedeutet dies alle Argumente der umschließenden Funktion. Im globalen (obersten) Bereich bedeutet dies alle Methoden, die anschließend im aktuellen Modul definiert werden.

Die Spezialisierung kann durch die Verwendung von [`@specialize`](@ref) auf den Standard zurückgesetzt werden.

```julia
function example_function(@nospecialize x)
    ...
end

function example_function(x, @nospecialize(y = 1))
    ...
end

function example_function(x, y, z)
    @nospecialize x y
    ...
end

@nospecialize
f(y) = [x for x in y]
@specialize
```

!!! Hinweis     `@nospecialize` beeinflusst die Codegenerierung, jedoch nicht die Inferenz: Es begrenzt die Vielfalt des resultierenden nativen Codes, auferlegt jedoch keine Einschränkungen (über die Standardbeschränkungen hinaus) bei der Typinferenz. Verwenden Sie [`Base.@nospecializeinfer`](@ref) zusammen mit `@nospecialize`, um zusätzlich die Inferenz zu unterdrücken.

# Beispiele

```julia
julia> f(A::AbstractArray) = g(A)
f (generische Funktion mit 1 Methode)

julia> @noinline g(@nospecialize(A::AbstractArray)) = A[1]
g (generische Funktion mit 1 Methode)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Float64
└──      return %1
) => Float64
```

Hier führt die Annotation `@nospecialize` zum Äquivalent von

```julia
f(A::AbstractArray) = invoke(g, Tuple{AbstractArray}, A)
```

was sicherstellt, dass nur eine Version des nativen Codes für `g` generiert wird, die generisch für jedes `AbstractArray` ist. Der spezifische Rückgabewert wird jedoch weiterhin sowohl für `g` als auch für `f` abgeleitet, und dies wird weiterhin zur Optimierung der Aufrufer von `f` und `g` verwendet.
