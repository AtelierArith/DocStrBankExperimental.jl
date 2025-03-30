```
AnnotatedString{S <: AbstractString} <: AbstractString
```

메타데이터가 있는 문자열, 주석이 달린 영역의 형태로.

더 구체적으로, 이는 주석이 달린 값으로 래핑된 문자열의 영역을 허용하는 다른 [`AbstractString`](@ref) 주위의 간단한 래퍼입니다.

```text
                           C
                    ┌──────┸─────────┐
  "this is an example annotated string"
  └──┰────────┼─────┘         │
     A        └─────┰─────────┘
                    B
```

위의 다이어그램은 세 개의 범위가 주석이 달린 `AnnotatedString`을 나타냅니다(라벨 `A`, `B`, 및 `C`로 표시됨). 각 주석은 라벨(`Symbol`)과 값(`Any`)을 보유합니다. 이 세 가지 정보는 `@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}`로 저장됩니다.

라벨은 고유할 필요가 없으며, 동일한 영역은 동일한 라벨을 가진 여러 주석을 가질 수 있습니다.

일반적으로 `AnnotatedString`에 대해 작성된 코드는 다음 속성을 보존해야 합니다:

  * 주석이 적용되는 문자
  * 각 문자에 주석이 적용되는 순서

추가적인 의미는 `AnnotatedString`의 특정 사용에 의해 도입될 수 있습니다.

이 규칙의 결과는 인접하고 연속적으로 배치된 동일한 라벨과 값을 가진 주석이 결합된 범위를 포괄하는 단일 주석과 동등하다는 것입니다.

또한 [`AnnotatedChar`](@ref), [`annotatedstring`](@ref), [`annotations`](@ref), 및 [`annotate!`](@ref)를 참조하십시오.

# 생성자

```julia
AnnotatedString(s::S<:AbstractString) -> AnnotatedString{S}
AnnotatedString(s::S<:AbstractString, annotations::Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}})
```

`AnnotatedString`은 또한 [`annotatedstring`](@ref)로 생성할 수 있으며, 이는 [`string`](@ref)와 유사하게 작동하지만 인수에 존재하는 모든 주석을 보존합니다.

# 예제

```julia-repl
julia> AnnotatedString("this is an example annotated string",
                    [(1:18, :A => 1), (12:28, :B => 2), (18:35, :C => 3)])
"this is an example annotated string"
```
