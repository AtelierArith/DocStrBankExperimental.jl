```
AtomicMemory{T} == GenericMemory{:atomic, T, Core.CPU}
```

Feste Größe [`DenseVector{T}`](@ref DenseVector). Der Zugriff auf eines seiner Elemente erfolgt atomar (mit `:monotonic` Ordnung). Das Setzen eines der Elemente muss unter Verwendung des `@atomic` Makros und unter expliziter Angabe der Ordnung erfolgen.

!!! warning
    Jedes Element ist unabhängig atomar, wenn es zugegriffen wird, und kann nicht nicht-atomar gesetzt werden. Derzeit sind das `@atomic` Makro und die höherstufige Schnittstelle noch nicht abgeschlossen, aber die Bausteine für eine zukünftige Implementierung sind die internen Intrinsics `Core.memoryrefget`, `Core.memoryrefset!`, `Core.memoryref_isassigned`, `Core.memoryrefswap!`, `Core.memoryrefmodify!` und `Core.memoryrefreplace!`.


Für Details siehe [Atomare Operationen](@ref man-atomic-operations)

!!! compat "Julia 1.11"
    Dieser Typ erfordert Julia 1.11 oder höher.

