```
Threads.atomic_or!(x::Atomic{T}, val::T) where T
```

`x`를 `val`과 원자적으로 비트wise-or합니다.

원자적으로 `x[] |= val`을 수행합니다. **이전** 값을 반환합니다.

자세한 내용은 LLVM의 `atomicrmw or` 명령어를 참조하십시오.

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_or!(x, 7)
5

julia> x[]
7
```
