```
@inline
```

Gibt dem Compiler einen Hinweis, dass diese Funktion es wert ist, inline zu sein.

Kleine Funktionen benötigen typischerweise nicht die `@inline`-Annotation, da der Compiler dies automatisch erledigt. Durch die Verwendung von `@inline` bei größeren Funktionen kann dem Compiler ein zusätzlicher Anstoß gegeben werden, sie inline zu machen.

`@inline` kann unmittelbar vor einer Funktionsdefinition oder innerhalb eines Funktionskörpers angewendet werden.

```julia
# annotiere lange Definition
@inline function longdef(x)
    ...
end

# annotiere kurze Definition
@inline shortdef(x) = ...

# annotiere anonyme Funktion, die ein `do`-Block erstellt
f() do
    @inline
    ...
end
```

!!! compat "Julia 1.8"
    Die Verwendung innerhalb eines Funktionskörpers erfordert mindestens Julia 1.8.


---

```
@inline block
```

Gibt dem Compiler einen Hinweis, dass Aufrufe innerhalb von `block` es wert sind, inline zu sein.

```julia
# Der Compiler wird versuchen, `f` inline zu machen
@inline f(...)

# Der Compiler wird versuchen, `f`, `g` und `+` inline zu machen
@inline f(...) + g(...)
```

!!! note
    Eine Aufrufstellen-Annotation hat immer Vorrang vor der Annotation, die auf die Definition der aufgerufenen Funktion angewendet wird:

    ```julia
    @noinline function explicit_noinline(args...)
        # Körper
    end

    let
        @inline explicit_noinline(args...) # wird inline gemacht
    end
    ```


!!! note
    Wenn es verschachtelte Aufrufstellen-Annotationen gibt, hat die innerste Annotation Vorrang:

    ```julia
    @noinline let a0, b0 = ...
        a = @inline f(a0)  # der Compiler wird versuchen, diesen Aufruf inline zu machen
        b = f(b0)          # der Compiler wird diesen Aufruf NICHT inline machen
        return a, b
    end
    ```


!!! warning
    Obwohl eine Aufrufstellen-Annotation versucht, das Inline zu erzwingen, unabhängig vom Kostenmodell, gibt es immer noch Chancen, dass es nicht gelingt. Besonders rekursive Aufrufe können nicht inline gemacht werden, selbst wenn sie als `@inline` annotiert sind.


!!! compat "Julia 1.8"
    Die Aufrufstellen-Annotation erfordert mindestens Julia 1.8.

