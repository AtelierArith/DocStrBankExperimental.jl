```
NamedTuple
```

`NamedTuple`은 이름에서 알 수 있듯이 이름이 있는 [`Tuple`](@ref)입니다. 즉, 각 항목이 고유한 이름을 가지는 튜플과 유사한 값의 모음입니다. 이름은 [`Symbol`](@ref)으로 표현됩니다. `Tuple`과 마찬가지로 `NamedTuple`은 불변입니다. 즉, 생성 후에는 이름이나 값을 제자리에서 수정할 수 없습니다.

이름이 있는 튜플은 키가 있는 튜플 리터럴로 생성할 수 있습니다. 예를 들어 `(a=1, b=2)`와 같이 생성하거나, 여는 괄호 뒤에 세미콜론이 있는 튜플 리터럴로 생성할 수 있습니다. 예를 들어 `(; a=1, b=2)` (이 형식은 아래에 설명된 대로 프로그래밍적으로 생성된 이름도 허용합니다) 또는 생성자로 `NamedTuple` 유형을 사용할 수 있습니다. 예를 들어 `NamedTuple{(:a, :b)}((1,2))`와 같이 생성할 수 있습니다.

이름이 있는 튜플에서 이름과 연결된 값을 접근하는 것은 필드 접근 구문을 사용하여 수행할 수 있습니다. 예를 들어 `x.a` 또는 [`getindex`](@ref)를 사용하여 `x[:a]` 또는 `x[(:a, :b)]`와 같이 접근할 수 있습니다. 이름의 튜플은 [`keys`](@ref)를 사용하여 얻을 수 있으며, 값의 튜플은 [`values`](@ref)를 사용하여 얻을 수 있습니다.

!!! note
    `NamedTuple`에 대한 반복은 이름 없이 *값*을 생성합니다. (아래 예를 참조하십시오.) 이름-값 쌍을 반복하려면 [`pairs`](@ref) 함수를 사용하십시오.


[`@NamedTuple`](@ref) 매크로는 `NamedTuple` 유형을 편리하게 선언하는 데 사용할 수 있습니다.

# 예제

```jldoctest
julia> x = (a=1, b=2)
(a = 1, b = 2)

julia> x.a
1

julia> x[:a]
1

julia> x[(:a,)]
(a = 1,)

julia> keys(x)
(:a, :b)

julia> values(x)
(1, 2)

julia> collect(x)
2-element Vector{Int64}:
 1
 2

julia> collect(pairs(x))
2-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
```

키워드 인수를 프로그래밍적으로 정의하는 방식과 유사하게, 이름이 있는 튜플은 세미콜론 뒤에 `name::Symbol => value` 쌍을 제공하여 생성할 수 있습니다. 이와 `name=value` 구문은 혼합할 수 있습니다:

```jldoctest
julia> (; :a => 1, :b => 2, c=3)
(a = 1, b = 2, c = 3)
```

이름-값 쌍은 이름이 있는 튜플을 스플래팅하거나 각 기호를 첫 번째 값으로 가지는 두 값의 컬렉션을 생성하는 반복자를 사용하여 제공할 수도 있습니다:

```jldoctest
julia> keys = (:a, :b, :c); values = (1, 2, 3);

julia> NamedTuple{keys}(values)
(a = 1, b = 2, c = 3)

julia> (; (keys .=> values)...)
(a = 1, b = 2, c = 3)

julia> nt1 = (a=1, b=2);

julia> nt2 = (c=3, d=4);

julia> (; nt1..., nt2..., b=20) # 최종 b는 nt1의 값을 덮어씁니다
(a = 1, b = 20, c = 3, d = 4)

julia> (; zip(keys, values)...) # zip은 (:a, 1)과 같은 튜플을 생성합니다
(a = 1, b = 2, c = 3)
```

키워드 인수와 마찬가지로, 식별자와 점 표현식은 이름을 암시합니다:

```jldoctest
julia> x = 0
0

julia> t = (; x)
(x = 0,)

julia> (; t.x)
(x = 0,)
```

!!! compat "Julia 1.5"
    식별자와 점 표현식에서의 암시적 이름은 Julia 1.5부터 사용할 수 있습니다.


!!! compat "Julia 1.7"
    여러 `Symbol`에 대한 `getindex` 메서드의 사용은 Julia 1.7부터 사용할 수 있습니다.

