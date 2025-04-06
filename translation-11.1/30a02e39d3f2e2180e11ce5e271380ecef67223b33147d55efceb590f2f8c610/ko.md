```
a ? b : c
```

조건부의 짧은 형태; "만약 `a`라면 `b`를 평가하고, 그렇지 않으면 `c`를 평가하라"고 읽습니다. [삼항 연산자](https://en.wikipedia.org/wiki/%3F:)로도 알려져 있습니다.

이 구문은 `if a; b else c end`와 동등하지만, 종종 더 큰 표현식의 일부로 사용되는 값 `b` 또는 `c`를 강조하기 위해 사용되며, `b` 또는 `c`를 평가하는 데 따른 부작용보다는 강조됩니다.

자세한 내용은 [제어 흐름](@ref man-conditional-evaluation) 매뉴얼 섹션을 참조하십시오.

# 예제

```jldoctest
julia> x = 1; y = 2;

julia> x > y ? println("x is larger") : println("x is not larger")
x is not larger

julia> x > y ? "x is larger" : x == y ? "x and y are equal" : "y is larger"
"y is larger"
```
