```
print([io::IO], xs...)
```

`io`에 (또는 `io`가 주어지지 않은 경우 기본 출력 스트림 [`stdout`](@ref)으로) 표준적인 (장식이 없는) 텍스트 표현을 씁니다. `print`에서 사용되는 표현은 최소한의 형식을 포함하며 Julia 특정 세부정보를 피하려고 합니다.

`print`는 `show`를 호출하는 것으로 대체되므로 대부분의 유형은 `show`만 정의하면 됩니다. 유형에 별도의 "일반" 표현이 있는 경우 `print`를 정의하십시오. 예를 들어, `show`는 문자열을 따옴표로 표시하고, `print`는 문자열을 따옴표 없이 표시합니다.

또한 [`println`](@ref), [`string`](@ref), [`printstyled`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> print("Hello World!")
Hello World!
julia> io = IOBuffer();

julia> print(io, "Hello", ' ', :World!)

julia> String(take!(io))
"Hello World!"
```
