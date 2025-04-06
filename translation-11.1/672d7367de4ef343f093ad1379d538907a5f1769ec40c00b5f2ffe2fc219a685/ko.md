```
@printf([io::IO], "%Fmt", args...)
```

C `printf` 스타일 포맷 지정 문자열을 사용하여 `args`를 출력합니다. 선택적으로, 출력 리디렉션을 위해 첫 번째 인수로 `IO`를 전달할 수 있습니다.

# 예제

```jldoctest
julia> @printf "Hello %s" "world"
Hello world

julia> @printf "Scientific notation %e" 1.234
Scientific notation 1.234000e+00

julia> @printf "Scientific notation three digits %.3e" 1.23456
Scientific notation three digits 1.235e+00

julia> @printf "Decimal two digits %.2f" 1.23456
Decimal two digits 1.23

julia> @printf "Padded to length 5 %5i" 123
Padded to length 5   123

julia> @printf "Padded with zeros to length 6 %06i" 123
Padded with zeros to length 6 000123

julia> @printf "Use shorter of decimal or scientific %g %g" 1.23 12300000.0
Use shorter of decimal or scientific 1.23 1.23e+07

julia> @printf "Use dynamic width and precision  %*.*f" 10 2 0.12345
Use dynamic width and precision        0.12
```

포맷의 체계적인 사양에 대해서는 [여기](https://en.cppreference.com/w/c/io/fprintf)를 참조하십시오. 출력 대신 `String`으로 결과를 얻으려면 [`@sprintf`](@ref)를 참조하십시오.

# 주의사항

`Inf`와 `NaN`은 플래그 `%a`, `%A`, `%e`, `%E`, `%f`, `%F`, `%g`, 및 `%G`에 대해 일관되게 `Inf`와 `NaN`으로 출력됩니다. 또한, 부동 소수점 숫자가 두 개의 가능한 출력 문자열의 숫자 값에 동일하게 가까운 경우, 0에서 더 멀리 떨어진 출력 문자열이 선택됩니다.

# 예제

```jldoctest
julia> @printf("%f %F %f %F", Inf, Inf, NaN, NaN)
Inf Inf NaN NaN

julia> @printf "%.0f %.1f %f" 0.5 0.025 -0.0078125
0 0.0 -0.007812
```

!!! compat "Julia 1.8"
    Julia 1.8부터 `%s` (문자열) 및 `%c` (문자) 너비는 [`textwidth`](@ref)를 사용하여 계산되며, 예를 들어 제로 너비 문자를 무시하고(예: 발음 기호를 위한 결합 문자) 특정 "넓은" 문자를 너비 `2`로 처리합니다(예: 이모지).


!!! compat "Julia 1.10"
    `%*s` 및 `%0*.*f`와 같은 동적 너비 지정자는 Julia 1.10이 필요합니다.


```
