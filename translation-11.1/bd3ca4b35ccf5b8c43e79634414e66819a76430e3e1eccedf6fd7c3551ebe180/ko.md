```
@MIME_str
```

[`MIME`](@ref) 유형을 작성하기 위한 편리한 매크로로, 일반적으로 [`show`](@ref)에 메서드를 추가할 때 사용됩니다. 예를 들어, `show(io::IO, ::MIME"text/html", x::MyType) = ...` 구문을 사용하여 `MyType`의 HTML 표현을 작성하는 방법을 정의할 수 있습니다.
