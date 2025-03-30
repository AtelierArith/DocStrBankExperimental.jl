```
@atomic var
@atomic order ex
```

`var` 또는 `ex`를 원자적으로 수행되도록 표시합니다. `ex`가 지원되는 표현식인 경우에만 해당합니다. `order`가 지정되지 않으면 기본값은 :sequentially_consistent입니다.

```
@atomic a.b.x = new
@atomic a.b.x += addend
@atomic :release a.b.x = new
@atomic :acquire_release a.b.x += addend
```

오른쪽에 표현된 저장 작업을 원자적으로 수행하고 새 값을 반환합니다.

`=`를 사용하면 이 작업은 `setproperty!(a.b, :x, new)` 호출로 변환됩니다. 다른 연산자를 사용할 경우 이 작업은 `modifyproperty!(a.b, :x, +, addend)[2]` 호출로 변환됩니다.

```
@atomic a.b.x max arg2
@atomic a.b.x + arg2
@atomic max(a.b.x, arg2)
@atomic :acquire_release max(a.b.x, arg2)
@atomic :acquire_release a.b.x + arg2
@atomic :acquire_release a.b.x max arg2
```

오른쪽에 표현된 이진 작업을 원자적으로 수행합니다. 결과를 첫 번째 인수의 필드에 저장하고 값 `(old, new)`를 반환합니다.

이 작업은 `modifyproperty!(a.b, :x, func, arg2)` 호출로 변환됩니다.

자세한 내용은 매뉴얼의 [Per-field atomics](@ref man-atomics) 섹션을 참조하십시오.

# 예제

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomic a.x # a의 필드 x를 가져오고, 순차적 일관성으로
1

julia> @atomic :sequentially_consistent a.x = 2 # a의 필드 x를 설정하고, 순차적 일관성으로
2

julia> @atomic a.x += 1 # a의 필드 x를 증가시키고, 순차적 일관성으로
3

julia> @atomic a.x + 1 # a의 필드 x를 증가시키고, 순차적 일관성으로
3 => 4

julia> @atomic a.x # a의 필드 x를 가져오고, 순차적 일관성으로
4

julia> @atomic max(a.x, 10) # a의 필드 x를 최대값으로 변경하고, 순차적 일관성으로
4 => 10

julia> @atomic a.x max 5 # 다시 a의 필드 x를 최대값으로 변경하고, 순차적 일관성으로
10 => 10
```

!!! compat "Julia 1.7"
    이 기능은 최소한 Julia 1.7이 필요합니다.

