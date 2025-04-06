```
Threads.atomic_sub!(x::Atomic{T}, val::T) where T <: ArithmeticTypes
```

`val`을 `x`에서 원자적으로 빼기

원자적으로 `x[] -= val`을 수행합니다. **이전** 값을 반환합니다. `Atomic{Bool}`에 대해서는 정의되어 있지 않습니다.

자세한 내용은 LLVM의 `atomicrmw sub` 명령어를 참조하십시오.

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_sub!(x, 2)
3

julia> x[]
1
```
