```
@NamedTuple{key1::Type1, key2::Type2, ...}
@NamedTuple begin key1::Type1; key2::Type2; ...; end
```

이 매크로는 `NamedTuple` 타입을 선언하는 더 편리한 구문을 제공합니다. 주어진 키와 타입을 가진 `NamedTuple` 타입을 반환하며, 이는 `NamedTuple{(:key1, :key2, ...), Tuple{Type1,Type2,...}}`와 동등합니다. `::Type` 선언이 생략되면 `Any`로 간주됩니다. `begin ... end` 형식은 선언을 여러 줄에 걸쳐 나눌 수 있게 해주며(구조체 선언과 유사), 그 외에는 동등합니다. `NamedTuple` 매크로는 `NamedTuple` 타입을 출력할 때 예를 들어 REPL에서 사용됩니다.

예를 들어, 튜플 `(a=3.1, b="hello")`는 타입 `NamedTuple{(:a, :b), Tuple{Float64, String}}`를 가지며, 이는 다음과 같이 `@NamedTuple`을 통해 선언할 수 있습니다:

```jldoctest
julia> @NamedTuple{a::Float64, b::String}
@NamedTuple{a::Float64, b::String}

julia> @NamedTuple begin
           a::Float64
           b::String
       end
@NamedTuple{a::Float64, b::String}
```

!!! compat "Julia 1.5"
    이 매크로는 Julia 1.5부터 사용할 수 있습니다.

