```
@noinline
```

Gibt dem Compiler einen Hinweis, dass er eine Funktion nicht inline setzen soll.

Kleine Funktionen werden typischerweise automatisch inline gesetzt. Durch die Verwendung von `@noinline` bei kleinen Funktionen kann das automatische Inlining verhindert werden.

`@noinline` kann unmittelbar vor einer Funktionsdefinition oder innerhalb eines Funktionskörpers angewendet werden.

```julia
# annotiere lange Definition
@noinline function longdef(x)
    ...
end

# annotiere kurze Definition
@noinline shortdef(x) = ...

# annotiere anonyme Funktion, die ein `do`-Block erstellt
f() do
    @noinline
    ...
end
```

!!! compat "Julia 1.8"
    Die Verwendung innerhalb eines Funktionskörpers erfordert mindestens Julia 1.8.


---

```
@noinline block
```

Gibt dem Compiler einen Hinweis, dass er die Aufrufe innerhalb von `block` nicht inline setzen soll.

```julia
# Der Compiler wird versuchen, `f` nicht inline zu setzen
@noinline f(...)

# Der Compiler wird versuchen, `f`, `g` und `+` nicht inline zu setzen
@noinline f(...) + g(...)
```

!!! note
    Eine Aufrufstellenannotation hat immer Vorrang vor der Annotation, die auf die Definition der aufgerufenen Funktion angewendet wird:

    ```julia
    @inline function explicit_inline(args...)
        # Körper
    end

    let
        @noinline explicit_inline(args...) # wird nicht inline gesetzt
    end
    ```


!!! note
    Wenn es verschachtelte Aufrufstellenannotationen gibt, hat die innerste Annotation Vorrang:

    ```julia
    @inline let a0, b0 = ...
        a = @noinline f(a0)  # der Compiler wird NICHT versuchen, diesen Aufruf inline zu setzen
        b = f(b0)            # der Compiler wird versuchen, diesen Aufruf inline zu setzen
        return a, b
    end
    ```


!!! compat "Julia 1.8"
    Die Aufrufstellenannotation erfordert mindestens Julia 1.8.


---

!!! note
    Wenn die Funktion trivial ist (zum Beispiel einen konstanten Wert zurückgibt), könnte sie trotzdem inline gesetzt werden.

