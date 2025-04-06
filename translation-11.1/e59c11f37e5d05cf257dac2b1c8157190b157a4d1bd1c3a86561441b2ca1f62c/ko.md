```
@show exs...
```

하나 이상의 표현식과 그 결과를 `stdout`에 출력하고, 마지막 결과를 반환합니다.

참고: [`show`](@ref), [`@info`](@ref man-logging), [`println`](@ref).

# 예제

```jldoctest
julia> x = @show 1+2
1 + 2 = 3
3

julia> @show x^2 x/2;
x ^ 2 = 9
x / 2 = 1.5
```
