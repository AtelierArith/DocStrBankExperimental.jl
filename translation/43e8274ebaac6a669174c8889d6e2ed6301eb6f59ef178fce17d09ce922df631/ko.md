```
AtomicMemory{T} == GenericMemory{:atomic, T, Core.CPU}
```

고정 크기 [`DenseVector{T}`](@ref DenseVector). 그 요소에 대한 접근은 원자적으로 수행됩니다( `:monotonic` 순서로). 요소 중 하나를 설정하려면 `@atomic` 매크로를 사용하고 명시적으로 순서를 지정해야 합니다.

!!! 경고     각 요소는 접근할 때 독립적으로 원자적이며 비원자적으로 설정할 수 없습니다. 현재 `@atomic` 매크로와 고급 인터페이스는 완료되지 않았지만, 향후 구현을 위한 빌딩 블록은 내부 내장 함수 `Core.memoryrefget`, `Core.memoryrefset!`, `Core.memoryref_isassigned`, `Core.memoryrefswap!`, `Core.memoryrefmodify!`, 및 `Core.memoryrefreplace!`입니다.

자세한 내용은 [Atomic Operations](@ref man-atomic-operations)를 참조하십시오.

!!! 호환성 "Julia 1.11"     이 유형은 Julia 1.11 이상이 필요합니다.
