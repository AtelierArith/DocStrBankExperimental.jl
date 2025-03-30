```
Threads.atomic_xor!(x::Atomic{T}, val::T) where T
```

원자적으로 `x`와 `val`을 비트 단위 XOR(배타적 OR)합니다.

`x[] $= val`을 원자적으로 수행합니다. **이전** 값을 반환합니다.

자세한 내용은 LLVM의 `atomicrmw xor` 명령어를 참조하십시오.

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(5)
Base.Threads.Atomic{Int64}(5)

julia> Threads.atomic_xor!(x, 7)
5

julia> x[]
2
```
