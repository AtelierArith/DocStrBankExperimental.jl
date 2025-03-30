# [Core.Builtins](@id lib-builtins)

## Builtin Function APIs

Aşağıdaki Yerleşik işlev API'leri istikrarsız olarak kabul edilmektedir, ancak bir Julia programının yeteneklerini ve davranışlarını tanımlayan temel tanımları sağlar. Genellikle daha yüksek seviyeli genel bir API aracılığıyla erişilir.

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
