```
@atomicswap a.b.x = new
@atomicswap :sequentially_consistent a.b.x = new
```

`new`을 `a.b.x`에 저장하고 `a.b.x`의 이전 값을 반환합니다.

이 작업은 `swapproperty!(a.b, :x, new)` 호출로 변환됩니다.

자세한 내용은 매뉴얼의 [Per-field atomics](@ref man-atomics) 섹션을 참조하세요.

# 예제

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicswap a.x = 2+2 # sequential consistency로 a의 필드 x를 4로 교체
1

julia> @atomic a.x # sequential consistency로 a의 필드 x를 가져옴
4
```

!!! compat "Julia 1.7"
    이 기능은 최소한 Julia 1.7이 필요합니다.

