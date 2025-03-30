```
Threads.atomic_nand!(x::Atomic{T}, val::T) where T
```

원자적으로 비트 단위 nand (not-and) 연산을 `x`와 `val`에 수행합니다.

`x[] = ~(x[] & val)`를 원자적으로 수행합니다. **이전** 값을 반환합니다.

자세한 내용은 LLVM의 `atomicrmw nand` 명령어를 참조하십시오.

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> Threads.atomic_nand!(x, 2)
3

julia> x[]
-3
```
