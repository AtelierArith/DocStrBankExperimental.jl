안전하지 않은 포인터 작업은 C11 및 C++23에서 각각 `_Atomic` 및 `std::atomic` 유형으로 선언된 포인터를 로드하고 저장하는 것과 호환됩니다. Julia 유형 `T`를 원자적으로 로드하는 것을 지원하지 않는 경우 오류가 발생할 수 있습니다.

참고: [`unsafe_load`](@ref), [`unsafe_modify!`](@ref), [`unsafe_replace!`](@ref), [`unsafe_store!`](@ref), [`unsafe_swap!`](@ref)
