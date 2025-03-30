```
lazy"str"
```

정규 문자열 보간법을 사용하여 [`LazyString`](@ref)를 생성합니다. 보간은 LazyString 생성 시점에 *평가*되지만, 문자열에 대한 첫 번째 접근이 있을 때까지 *출력*은 지연됩니다.

동시 프로그램에 대한 안전성 속성에 대한 [`LazyString`](@ref) 문서를 참조하십시오.

# 예제

```
julia> n = 5; str = lazy"n is $n"
"n is 5"

julia> typeof(str)
LazyString
```

!!! compat "Julia 1.8"
    `lazy"str"`는 Julia 1.8 이상이 필요합니다.

