```
parse(type, str; base)
```

문자열을 숫자로 파싱합니다. `Integer` 유형의 경우, 진수를 지정할 수 있습니다(기본값은 10입니다). 부동 소수점 유형의 경우, 문자열은 10진 부동 소수점 숫자로 파싱됩니다. `Complex` 유형은 `"R±Iim"` 형식의 10진 문자열에서 `Complex(R,I)`로 요청된 유형으로 파싱됩니다; `"i"` 또는 `"j"`를 `"im"` 대신 사용할 수 있으며, `"R"` 또는 `"Iim"`도 허용됩니다. 문자열에 유효한 숫자가 포함되어 있지 않으면 오류가 발생합니다.

!!! compat "Julia 1.1"
    `parse(Bool, str)`는 최소한 Julia 1.1이 필요합니다.


# 예제

```jldoctest
julia> parse(Int, "1234")
1234

julia> parse(Int, "1234", base = 5)
194

julia> parse(Int, "afc", base = 16)
2812

julia> parse(Float64, "1.2e-3")
0.0012

julia> parse(Complex{Float64}, "3.2e-1 + 4.5im")
0.32 + 4.5im
```
