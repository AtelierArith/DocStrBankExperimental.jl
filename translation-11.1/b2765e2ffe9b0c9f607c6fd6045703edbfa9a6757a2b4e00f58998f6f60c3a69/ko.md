```
Threads.atomic_xchg!(x::Atomic{T}, newval::T) where T
```

`x`의 값을 원자적으로 교환합니다.

`x`의 값을 `newval`과 원자적으로 교환합니다. **이전** 값을 반환합니다.

자세한 내용은 LLVM의 `atomicrmw xchg` 명령어를 참조하십시오.

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_xchg!(x, 2)
3

julia> x[]
2
```
