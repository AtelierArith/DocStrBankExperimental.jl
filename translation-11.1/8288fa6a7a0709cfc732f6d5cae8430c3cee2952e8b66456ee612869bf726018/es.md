# [Core.Builtins](@id lib-builtins)

## Builtin Function APIs

Las siguientes APIs de funciones integradas se consideran inestables, pero proporcionan las definiciones básicas de lo que define las habilidades y comportamientos de un programa Julia. Generalmente se accede a ellas a través de una API genérica de nivel superior.

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
