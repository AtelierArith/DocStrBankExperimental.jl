# [Core.Builtins](@id lib-builtins)

## Builtin Function APIs

Les API de fonctions intégrées suivantes sont considérées comme instables, mais fournissent les définitions de base de ce qui définit les capacités et les comportements d'un programme Julia. Elles sont généralement accessibles via une API générique de niveau supérieur.

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
