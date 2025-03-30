```
string(n::Integer; base::Integer = 10, pad::Integer = 1)
```

정수 `n`을 주어진 `base`의 문자열로 변환하며, 선택적으로 패딩할 자릿수를 지정할 수 있습니다.

자세한 내용은 [`digits`](@ref), [`bitstring`](@ref), [`count_zeros`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> string(5, base = 13, pad = 4)
"0005"

julia> string(-13, base = 5, pad = 4)
"-0023"
```
