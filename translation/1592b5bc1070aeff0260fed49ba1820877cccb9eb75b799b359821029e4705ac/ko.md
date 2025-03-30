```
@atomicreplace a.b.x expected => desired
@atomicreplace :sequentially_consistent a.b.x expected => desired
@atomicreplace :sequentially_consistent :monotonic a.b.x expected => desired
```

조건부 교체를 쌍으로 원자적으로 수행하여 `(old, success::Bool)` 값을 반환합니다. 여기서 `success`는 교체가 완료되었는지를 나타냅니다.

이 작업은 `replaceproperty!(a.b, :x, expected, desired)` 호출로 변환됩니다.

자세한 내용은 매뉴얼의 [Per-field atomics](@ref man-atomics) 섹션을 참조하세요.

# 예제

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicreplace a.x 1 => 2 # a의 필드 x를 1일 경우 2로 교체, 순차적 일관성 유지
(old = 1, success = true)

julia> @atomic a.x # a의 필드 x를 가져오기, 순차적 일관성 유지
2

julia> @atomicreplace a.x 1 => 2 # a의 필드 x를 1일 경우 2로 교체, 순차적 일관성 유지
(old = 2, success = false)

julia> xchg = 2 => 0; # a의 필드 x를 2일 경우 0으로 교체, 순차적 일관성 유지

julia> @atomicreplace a.x xchg
(old = 2, success = true)

julia> @atomic a.x # a의 필드 x를 가져오기, 순차적 일관성 유지
0
```

!!! compat "Julia 1.7"
    이 기능은 최소한 Julia 1.7이 필요합니다.

