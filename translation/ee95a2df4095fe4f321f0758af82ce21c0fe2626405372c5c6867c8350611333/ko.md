```
ndigits(n::Integer; base::Integer=10, pad::Integer=1)
```

정수 `n`을 `base` 진수로 썼을 때의 자릿수를 계산합니다 (`base`는 `[-1, 0, 1]`이 아니어야 함) 그리고 선택적으로 지정된 크기로 0으로 패딩할 수 있습니다 (결과는 결코 `pad`보다 작지 않습니다).

자세한 내용은 [`digits`](@ref), [`count_ones`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> ndigits(0)
1

julia> ndigits(12345)
5

julia> ndigits(1022, base=16)
3

julia> string(1022, base=16)
"3fe"

julia> ndigits(123, pad=5)
5

julia> ndigits(-123)
3
```
