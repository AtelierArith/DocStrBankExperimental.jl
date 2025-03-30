```
annotatedstring(values...)
```

`values`의 [`print`](@ref)된 표현을 사용하여 `AnnotatedString`을 생성합니다.

이것은 [`string`](@ref)처럼 작동하지만, 존재하는 모든 주석(형태가 [`AnnotatedString`](@ref) 또는 [`AnnotatedChar`](@ref) 값인)을 보존하는 데 주의합니다.

또한 [`AnnotatedString`](@ref) 및 [`AnnotatedChar`](@ref)를 참조하십시오.

## 예제

```julia-repl
julia> annotatedstring("now a AnnotatedString")
"now a AnnotatedString"

julia> annotatedstring(AnnotatedString("annotated", [(1:9, :label => 1)]), ", and unannotated")
"annotated, and unannotated"
```
