```
binomial(x::Number, k::Integer)
```

일반화된 이항 계수는 `k ≥ 0`에 대해 다항식으로 정의됩니다.

$$
\frac{1}{k!} \prod_{j=0}^{k-1} (x - j)
$$

`k < 0`인 경우에는 0을 반환합니다.

정수 `x`의 경우, 이는 일반적인 정수 이항 계수와 동등합니다.

$$
\binom{n}{k} = \frac{n!}{k! (n-k)!}
$$

비정수 `k`에 대한 추가 일반화는 수학적으로 가능하지만, 감마 함수 및/또는 베타 함수를 포함하며, 이는 Julia 표준 라이브러리에서 제공되지 않지만 [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl)과 같은 외부 패키지에서 사용할 수 있습니다.

# 외부 링크

  * [이항 계수](https://en.wikipedia.org/wiki/Binomial_coefficient) 위키백과.
