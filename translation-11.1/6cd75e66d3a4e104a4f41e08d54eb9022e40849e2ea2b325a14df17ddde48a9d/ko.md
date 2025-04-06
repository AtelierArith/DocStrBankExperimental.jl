```
rpad(s, n::Integer, p::Union{AbstractChar,AbstractString}=' ') -> String
```

`s`를 문자열로 변환하고 결과 문자열의 오른쪽에 `p`로 패딩하여 `n` 문자( [`textwidth`](@ref) ) 길이를 만듭니다. 만약 `s`가 이미 `n` 문자 길이라면, 동일한 문자열이 반환됩니다. 기본적으로 공백으로 패딩합니다.

# 예제

```jldoctest
julia> rpad("March", 20)
"March               "
```

!!! compat "Julia 1.7"
    Julia 1.7에서는 이 함수가 원시 문자(코드포인트) 수 대신 `textwidth`를 사용하도록 변경되었습니다.

