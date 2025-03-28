```
GenericMemory{kind::Symbol, T, addrspace=Core.CPU} <: DenseVector{T}
```

Feste Größe [`DenseVector{T}`](@ref DenseVector).

`kind` kann derzeit entweder `:not_atomic` oder `:atomic` sein. Für Details zu dem, was `:atomic` impliziert, siehe [`AtomicMemory`](@ref)

`addrspace` kann derzeit nur auf Core.CPU gesetzt werden. Es ist so konzipiert, dass es die Erweiterung durch andere Systeme wie GPUs ermöglicht, die Werte wie folgt definieren könnten:

```
module CUDA
const Generic = bitcast(Core.AddrSpace{CUDA}, 0)
const Global = bitcast(Core.AddrSpace{CUDA}, 1)
end
```

Die genauen Semantiken dieser anderen addrspaces werden durch das spezifische Backend definiert, aber es wird einen Fehler geben, wenn der Benutzer versucht, diese auf der CPU zuzugreifen.

!!! compat "Julia 1.11"
    Dieser Typ erfordert Julia 1.11 oder höher.

