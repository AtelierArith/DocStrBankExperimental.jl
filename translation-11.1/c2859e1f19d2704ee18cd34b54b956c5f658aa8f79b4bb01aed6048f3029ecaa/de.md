```
finalizer(f, x)
```

Registrieren Sie eine Funktion `f(x)`, die aufgerufen wird, wenn es keine programmzugänglichen Referenzen zu `x` mehr gibt, und geben Sie `x` zurück. Der Typ von `x` muss eine `mutable struct` sein, andernfalls wird die Funktion einen Fehler auslösen.

`f` darf keinen Taskwechsel verursachen, was die meisten I/O-Operationen wie `println` ausschließt. Die Verwendung des `@async`-Makros (um den Kontextwechsel außerhalb des Finalizers zu verschieben) oder `ccall`, um I/O-Funktionen in C direkt aufzurufen, kann zu Debugging-Zwecken hilfreich sein.

Beachten Sie, dass es kein garantierter Weltalter für die Ausführung von `f` gibt. Es kann im Weltalter aufgerufen werden, in dem der Finalizer registriert wurde, oder in einem späteren Weltalter.

# Beispiele

```julia
finalizer(my_mutable_struct) do x
    @async println("Finalizing $x.")
end

finalizer(my_mutable_struct) do x
    ccall(:jl_safe_printf, Cvoid, (Cstring, Cstring), "Finalizing %s.", repr(x))
end
```

Ein Finalizer kann bei der Objektkonstruktion registriert werden. Im folgenden Beispiel beachten Sie, dass wir implizit darauf vertrauen, dass der Finalizer die neu erstellte mutable struct `x` zurückgibt.

```julia
mutable struct MyMutableStruct
    bar
    function MyMutableStruct(bar)
        x = new(bar)
        f(t) = @async println("Finalizing $t.")
        finalizer(f, x)
    end
end
```
