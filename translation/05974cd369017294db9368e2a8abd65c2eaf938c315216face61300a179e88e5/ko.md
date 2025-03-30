```
show(io::IO, mime, x)
```

[`display`](@ref) 함수는 궁극적으로 객체 `x`를 주어진 I/O 스트림 `io`(보통 메모리 버퍼)에 주어진 `mime` 유형으로 쓰기 위해 `show`를 호출합니다. 사용자 정의 유형 `T`의 풍부한 멀티미디어 표현을 제공하기 위해서는 `T`에 대한 새로운 `show` 메서드를 정의하기만 하면 됩니다. 방법은 다음과 같습니다: `show(io, ::MIME"mime", x::T) = ...`, 여기서 `mime`은 MIME 유형 문자열이며 함수 본문은 [`write`](@ref) (또는 유사한 함수)를 호출하여 `x`의 해당 표현을 `io`에 씁니다. (`MIME""` 표기법은 리터럴 문자열만 지원하므로, 더 유연한 방식으로 `MIME` 유형을 구성하려면 `MIME{Symbol("")}`을 사용하세요.)

예를 들어, `MyImage` 유형을 정의하고 이를 PNG 파일로 쓰는 방법을 알고 있다면, `show(io, ::MIME"image/png", x::MyImage) = ...` 함수를 정의하여 PNG를 지원하는 모든 `AbstractDisplay`(예: IJulia)에서 이미지를 표시할 수 있도록 할 수 있습니다. 항상 그렇듯이, 내장된 Julia 함수 `show`에 새로운 메서드를 추가하려면 `import Base.show`를 잊지 마세요.

기술적으로, `MIME"mime"` 매크로는 주어진 `mime` 문자열에 대한 단일 유형을 정의하여, 주어진 유형의 객체를 표시하는 방법을 결정하는 데 Julia의 분산 메커니즘을 활용할 수 있게 합니다.

기본 MIME 유형은 `MIME"text/plain"`입니다. `text/plain` 출력을 위한 대체 정의가 있으며, 이는 2개의 인수로 `show`를 호출하므로 항상 해당 경우에 대한 메서드를 추가할 필요는 없습니다. 그러나 유형이 사용자에게 읽기 쉬운 출력의 이점을 누린다면, `show(::IO, ::MIME"text/plain", ::T)`를 정의해야 합니다. 예를 들어, `Day` 유형은 `text/plain` MIME 유형에 대해 `1 day`를 출력으로 사용하며, `Day(1)`은 2-인수 `show`의 출력입니다.

# 예제

```jldoctest
julia> struct Day
           n::Int
       end

julia> Base.show(io::IO, ::MIME"text/plain", d::Day) = print(io, d.n, " day")

julia> Day(1)
1 day
```

컨테이너 유형은 일반적으로 `show(io, MIME"text/plain"(), x)`를 호출하여 요소 `x`에 대해 3-인수 `show`를 구현하며, 첫 번째 인수로 전달된 [`IOContext`](@ref)에서 `:compact => true`가 설정됩니다.
