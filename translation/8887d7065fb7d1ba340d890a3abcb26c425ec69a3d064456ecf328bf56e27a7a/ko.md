```
@kwdef typedef
```

이 매크로는 `typedef` 표현식에서 선언된 타입에 대한 키워드 기반 생성자를 자동으로 정의하는 도우미 매크로입니다. 여기서 `typedef`는 `struct` 또는 `mutable struct` 표현식이어야 합니다. 기본 인자는 `field::T = default` 또는 `field = default` 형식으로 필드를 선언하여 제공됩니다. 기본값이 제공되지 않으면 키워드 인자는 결과 타입 생성자에서 필수 키워드 인자가 됩니다.

내부 생성자는 여전히 정의할 수 있지만, 적어도 하나는 기본 내부 생성자와 동일한 형식(즉, 필드당 하나의 위치 인자)을 수용해야 키워드 외부 생성자와 올바르게 작동합니다.

!!! compat "Julia 1.1"
    매개변수화된 구조체 및 수퍼타입이 있는 구조체에 대한 `Base.@kwdef`는 최소한 Julia 1.1이 필요합니다.


!!! compat "Julia 1.9"
    이 매크로는 Julia 1.9부터 내보내집니다.


# 예제

```jldoctest
julia> @kwdef struct Foo
           a::Int = 1         # 지정된 기본값
           b::String          # 필수 키워드
       end
Foo

julia> Foo(b="hi")
Foo(1, "hi")

julia> Foo()
ERROR: UndefKeywordError: keyword argument `b` not assigned
Stacktrace:
[...]
```
