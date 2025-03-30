```
@atomiconce a.b.x = value
@atomiconce :sequentially_consistent a.b.x = value
@atomiconce :sequentially_consistent :monotonic a.b.x = value
```

값이 이전에 설정되지 않은 경우, 조건부 할당을 원자적으로 수행하고 `success::Bool` 값을 반환합니다. 여기서 `success`는 할당이 완료되었는지를 나타냅니다.

이 작업은 `setpropertyonce!(a.b, :x, value)` 호출로 변환됩니다.

자세한 내용은 매뉴얼의 [Per-field atomics](@ref man-atomics) 섹션을 참조하십시오.

# 예제

```jldoctest
julia> mutable struct AtomicOnce
           @atomic x
           AtomicOnce() = new()
       end

julia> a = AtomicOnce()
AtomicOnce(#undef)

julia> @atomiconce a.x = 1 # 설정되지 않은 경우, 순차적 일관성으로 a의 필드 x를 1로 설정
true

julia> @atomic a.x # 순차적 일관성으로 a의 필드 x를 가져오기
1

julia> @atomiconce a.x = 1 # 설정되지 않은 경우, 순차적 일관성으로 a의 필드 x를 1로 설정
false
```

!!! compat "Julia 1.11"
    이 기능은 최소한 Julia 1.11이 필요합니다.


```
