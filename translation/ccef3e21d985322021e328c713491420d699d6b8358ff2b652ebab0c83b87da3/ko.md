```
Threads.atomic_min!(x::Atomic{T}, val::T) where T
```

`x`와 `val`의 최소값을 원자적으로 `x`에 저장합니다.

`x[] = min(x[], val)`을 원자적으로 수행합니다. **이전** 값을 반환합니다.

자세한 내용은 LLVM의 `atomicrmw min` 명령어를 참조하십시오.

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(7)
Base.Threads.Atomic{Int64}(7)

julia> Threads.atomic_min!(x, 5)
7

julia> x[]
5
```
