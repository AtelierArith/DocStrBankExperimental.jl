```
binomial(n::Integer, k::Integer)
```

*이항 계수* $\binom{n}{k}$는 $(1+x)^n$의 다항식 전개에서 $k$번째 항의 계수입니다.

만약 $n$이 비음이 아닌 경우, 이는 `n` 항목 중 `k`를 선택하는 방법의 수입니다:

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

여기서 $n!$는 [`factorial`](@ref) 함수입니다.

만약 $n$이 음수인 경우, 이는 다음의 항등식으로 정의됩니다:

$$
\binom{n}{k} = (-1)^k \binom{k-n-1}{k}
$$

자세한 내용은 [`factorial`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> binomial(5, 3)
10

julia> factorial(5) ÷ (factorial(5-3) * factorial(3))
10

julia> binomial(-5, 3)
-35
```

# 외부 링크

  * [이항 계수](https://en.wikipedia.org/wiki/Binomial_coefficient) 위키백과.
