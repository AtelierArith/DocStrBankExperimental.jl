```
Threads.atomic_max!(x::Atomic{T}, val::T) where T
```

`x`와 `val`의 최대값을 원자적으로 `x`에 저장합니다.

원자적으로 `x[] = max(x[], val)`을 수행합니다. **이전** 값을 반환합니다.

자세한 내용은 LLVM의 `atomicrmw max` 명령어를 참조하십시오.

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_max!(x, 7)
5

julia> x[]
7
```
