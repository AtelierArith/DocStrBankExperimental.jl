```
GenericMemory{kind::Symbol, T, addrspace=Core.CPU} <: DenseVector{T}
```

고정 크기 [`DenseVector{T}`](@ref DenseVector).

`kind`는 현재 `:not_atomic` 또는 `:atomic`일 수 있습니다. `:atomic`이 의미하는 바에 대한 자세한 내용은 [`AtomicMemory`](@ref)를 참조하십시오.

`addrspace`는 현재 Core.CPU로만 설정할 수 있습니다. 이는 GPU와 같은 다른 시스템에 의해 확장이 가능하도록 설계되었으며, 이러한 시스템은 다음과 같은 값을 정의할 수 있습니다:

```
module CUDA
const Generic = bitcast(Core.AddrSpace{CUDA}, 0)
const Global = bitcast(Core.AddrSpace{CUDA}, 1)
end
```

이러한 다른 addrspace의 정확한 의미는 특정 백엔드에 의해 정의되지만, 사용자가 CPU에서 이를 접근하려고 할 경우 오류가 발생합니다.

!!! compat "Julia 1.11"
    이 유형은 Julia 1.11 이상이 필요합니다.

