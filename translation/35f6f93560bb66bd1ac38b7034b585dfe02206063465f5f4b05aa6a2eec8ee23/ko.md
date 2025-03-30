```
evalpoly(x, p)
```

다항식 $\sum_k x^{k-1} p[k]$를 평가합니다. 여기서 계수는 `p[1]`, `p[2]`, ...로 주어지며, 즉 계수는 `x`의 거듭제곱에 따라 오름차순으로 주어집니다. 계수의 수가 정적으로 알려져 있을 때, 즉 `p`가 `Tuple`일 때 루프는 컴파일 시간에 펼쳐집니다. 이 함수는 `x`가 실수일 때 호너의 방법을 사용하여 효율적인 코드를 생성하거나, `x`가 복소수일 때 Goertzel과 유사한 [^DK62] 알고리즘을 사용하여 효율적인 코드를 생성합니다.

[^DK62]: Donald Knuth, Art of Computer Programming, Volume 2: Seminumerical Algorithms, Sec. 4.6.4.

!!! compat "Julia 1.4"
    이 함수는 Julia 1.4 이상이 필요합니다.


# 예제

```jldoctest
julia> evalpoly(2, (1, 2, 3))
17
```
