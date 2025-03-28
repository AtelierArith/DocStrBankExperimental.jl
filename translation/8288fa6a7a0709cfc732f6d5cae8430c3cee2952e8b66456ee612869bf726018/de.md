# [Core.Builtins](@id lib-builtins)

## Builtin Function APIs

Die folgenden Builtin-Funktions-APIs gelten als instabil, bieten jedoch die grundlegenden Definitionen dafür, was die Fähigkeiten und Verhaltensweisen eines Julia-Programms definiert. Sie werden typischerweise über eine höherstufige generische API aufgerufen.

```@docs
Core.memoryrefnew
Core.memoryrefoffset
Core.memoryrefget
Core.memoryrefset!
Core.memoryref_isassigned
Core.memoryrefswap!
Core.memoryrefmodify!
Core.memoryrefreplace!
Core.memoryrefsetonce!
Core.Intrinsics.atomic_pointerref
Core.Intrinsics.atomic_pointerset
Core.Intrinsics.atomic_pointerswap
Core.Intrinsics.atomic_pointermodify
Core.Intrinsics.atomic_pointerreplace
Core.get_binding_type
Core.set_binding_type!
Core.IntrinsicFunction
Core.Intrinsics
Core.IR
```
