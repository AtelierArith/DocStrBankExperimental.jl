# [Core.Builtins](@id lib-builtins)

## Builtin Function APIs

다음의 내장 함수 API는 불안정한 것으로 간주되지만, Julia 프로그램의 능력과 동작을 정의하는 기본 정의를 제공합니다. 이들은 일반적으로 더 높은 수준의 일반 API를 통해 접근됩니다.

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
