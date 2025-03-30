```
range(start, stop, length)
range(start, stop; length, step)
range(start; length, stop, step)
range(;start, length, stop, step)
```

인수로부터 균등 간격의 요소와 최적화된 저장소를 가진 특수화된 배열 (즉, [`AbstractRange`](@ref))을 생성합니다. 수학적으로 범위는 `start`, `step`, `stop` 및 `length` 중 임의의 세 개에 의해 고유하게 결정됩니다. 유효한 범위 호출은 다음과 같습니다:

  * `start`, `step`, `stop`, `length` 중 임의의 세 개로 `range`를 호출합니다.
  * `start`, `stop`, `length` 중 두 개로 `range`를 호출합니다. 이 경우 `step`은 1로 가정됩니다. 두 인수가 정수인 경우 [`UnitRange`](@ref)가 반환됩니다.
  * `stop` 또는 `length` 중 하나로 `range`를 호출합니다. `start`와 `step`은 1로 가정됩니다.

반환된 유형에 대한 추가 세부정보는 확장 도움말을 참조하십시오. 로그 간격의 점에 대해서는 [`logrange`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> range(1, length=100)
1:100

julia> range(1, stop=100)
1:100

julia> range(1, step=5, length=100)
1:5:496

julia> range(1, step=5, stop=100)
1:5:96

julia> range(1, 10, length=101)
1.0:0.09:10.0

julia> range(1, 100, step=5)
1:5:96

julia> range(stop=10, length=5)
6:10

julia> range(stop=10, step=1, length=5)
6:1:10

julia> range(start=1, step=1, stop=10)
1:1:10

julia> range(; length = 10)
Base.OneTo(10)

julia> range(; stop = 6)
Base.OneTo(6)

julia> range(; stop = 6.5)
1.0:1.0:6.0
```

`length`가 지정되지 않고 `stop - start`가 `step`의 정수 배수가 아닌 경우, `stop` 이전에 끝나는 범위가 생성됩니다.

```jldoctest
julia> range(1, 3.5, step=2)
1.0:2.0:3.0
```

중간 값이 합리적으로 계산되도록 특별한 주의가 기울여집니다. 이로 인한 오버헤드를 피하려면 [`LinRange`](@ref) 생성자를 참조하십시오.

!!! compat "Julia 1.1"
    위치 인수로서의 `stop`은 최소한 Julia 1.1이 필요합니다.


!!! compat "Julia 1.7"
    키워드 인수가 없는 버전과 `start`가 키워드 인수인 버전은 최소한 Julia 1.7이 필요합니다.


!!! compat "Julia 1.8"
    `stop`이 유일한 키워드 인수인 버전 또는 `length`가 유일한 키워드 인수인 버전은 최소한 Julia 1.8이 필요합니다.


# 확장 도움말

`range`는 인수가 정수일 때 `Base.OneTo`를 생성합니다.

  * 오직 `length`만 제공된 경우
  * 오직 `stop`만 제공된 경우

`range`는 인수가 정수일 때 `UnitRange`를 생성합니다.

  * 오직 `start`와 `stop`만 제공된 경우
  * 오직 `length`와 `stop`만 제공된 경우

`step`이 제공된 경우, 심지어 1로 지정되더라도 `UnitRange`는 생성되지 않습니다.
