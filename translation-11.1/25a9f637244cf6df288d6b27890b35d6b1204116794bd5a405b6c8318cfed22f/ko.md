```
hypot(x, y)
```

두 변의 길이가 각각 $|x|$와 $|y|$인 직각삼각형의 빗변의 길이 $\sqrt{|x|^2+|y|^2}$를 계산합니다. 오버플로우와 언더플로우를 피합니다.

이 코드는 Carlos F. Borges의 `hypot(a,b)`에 대한 개선된 알고리즘을 설명하는 논문의 구현입니다. 이 기사는 arXiv에서 온라인으로 확인할 수 있으며, 링크는 https://arxiv.org/abs/1904.09481입니다.

```
hypot(x...)
```

여러 변의 길이가 각각 $|x_i|$인 직각삼각형의 빗변의 길이 $\sqrt{\sum |x_i|^2}$를 계산합니다. 오버플로우와 언더플로우를 피합니다.

또한 [`LinearAlgebra`](@ref man-linalg) 표준 라이브러리의 `norm`을 참조하세요.

# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> a = Int64(10)^10;

julia> hypot(a, a)
1.4142135623730951e10

julia> √(a^2 + a^2) # a^2가 오버플로우 발생
ERROR: DomainError with -2.914184810805068e18:
sqrt는 음의 실수 인수로 호출되었지만, 복소수 인수로 호출될 경우에만 복소수 결과를 반환합니다. sqrt(Complex(x))를 시도해 보세요.
Stacktrace:
[...]

julia> hypot(3, 4im)
5.0

julia> hypot(-5.7)
5.7

julia> hypot(3, 4im, 12.0)
13.0

julia> using LinearAlgebra

julia> norm([a, a, a, a]) == hypot(a, a, a, a)
true
```
