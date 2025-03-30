# Talking to the compiler (the `:meta` mechanism)

일부 상황에서는 주어진 코드 블록이 특별한 속성을 가지고 있다는 힌트나 지침을 제공하고 싶을 수 있습니다: 항상 인라인으로 처리하거나 특별한 컴파일러 최적화 패스를 활성화하고 싶을 수 있습니다. 0.4 버전부터, Julia는 이러한 지침을 `:meta` 표현식 안에 배치할 수 있는 규칙을 가지고 있으며, 이는 일반적으로 (그러나 반드시 그렇지는 않음) 함수 본문의 첫 번째 표현식입니다.

`:meta` 표현식은 매크로로 생성됩니다. 예를 들어, `@inline` 매크로의 구현을 고려해 보십시오:

```julia
macro inline(ex)
    esc(isa(ex, Expr) ? pushmeta!(ex, :inline) : ex)
end
```

여기서 `ex`는 함수를 정의하는 표현식으로 예상됩니다. 다음과 같은 문장:

```julia
@inline function myfunction(x)
    x*(x+3)
end
```

이런 표현으로 변환됩니다:

```julia
quote
    function myfunction(x)
        Expr(:meta, :inline)
        x*(x+3)
    end
end
```

`Base.pushmeta!(ex, tag::Union{Symbol,Expr})`는 `:meta` 표현식의 끝에 `:tag`를 추가하며, 필요할 경우 새로운 `:meta` 표현식을 생성합니다.

메타데이터를 사용하려면 이러한 `:meta` 표현식을 파싱해야 합니다. 구현이 Julia 내에서 수행될 수 있다면, `Base.popmeta!`가 매우 유용합니다: `Base.popmeta!(body, :symbol)`는 함수 *body* 표현식(함수 시그니처가 없는 것)을 스캔하여 `:symbol`을 포함하는 첫 번째 `:meta` 표현식을 찾아 인수를 추출하고 튜플 `(found::Bool, args::Array{Any})`를 반환합니다. 메타데이터에 인수가 없거나 `:symbol`이 발견되지 않으면 `args` 배열은 비어 있게 됩니다.

아직 제공되지 않은 것은 C++에서 `:meta` 표현식을 파싱하기 위한 편리한 인프라입니다.
