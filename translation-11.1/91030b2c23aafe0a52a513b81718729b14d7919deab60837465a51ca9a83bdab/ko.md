```
factorial(n::Integer)
```

`n`의 팩토리얼. `n`이 [`Integer`](@ref)인 경우, 팩토리얼은 정수로 계산되며 (최소 64비트로 승격됨) `n`이 작지 않으면 오버플로우가 발생할 수 있습니다. 그러나 `factorial(big(n))`을 사용하여 임의의 정밀도로 결과를 정확하게 계산할 수 있습니다.

또한 [`binomial`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> factorial(6)
720

julia> factorial(21)
ERROR: OverflowError: 21 is too large to look up in the table; consider using `factorial(big(21))` instead
Stacktrace:
[...]

julia> factorial(big(21))
51090942171709440000
```

# 외부 링크

  * [팩토리얼](https://en.wikipedia.org/wiki/Factorial) 위키백과.
