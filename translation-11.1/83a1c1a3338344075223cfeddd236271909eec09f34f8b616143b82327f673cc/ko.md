```
Threads.atomic_and!(x::Atomic{T}, val::T) where T
```

`x`와 `val`을 원자적으로 비트 단위 AND 연산합니다.

원자적으로 `x[] &= val`을 수행합니다. **이전** 값을 반환합니다.

자세한 내용은 LLVM의 `atomicrmw and` 명령어를 참조하십시오.

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_and!(x, 2)
3

julia> x[]
2
```
