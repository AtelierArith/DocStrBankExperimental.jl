```
include_string([mapexpr::Function,] m::Module, code::AbstractString, filename::AbstractString="string")
```

[`include`](@ref)와 유사하지만, 파일이 아닌 주어진 문자열에서 코드를 읽습니다.

선택적 첫 번째 인수 `mapexpr`는 포함된 코드를 평가하기 전에 변환하는 데 사용할 수 있습니다: `code`에서 구문 분석된 각 표현식 `expr`에 대해 `include_string` 함수는 실제로 `mapexpr(expr)`을 평가합니다. 생략할 경우, `mapexpr`는 기본적으로 [`identity`](@ref)로 설정됩니다.

!!! compat "Julia 1.5"
    `mapexpr` 인수를 전달하려면 Julia 1.5가 필요합니다.

