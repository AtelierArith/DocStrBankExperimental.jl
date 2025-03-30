```
dot(x, y)
x ⋅ y
```

두 벡터 간의 내적을 계산합니다. 복소 벡터의 경우, 첫 번째 벡터는 켤레화됩니다.

`dot`은 요소에 대해 `dot`이 정의되어 있는 한, 모든 차원의 배열을 포함한 임의의 반복 가능한 객체에서도 작동합니다.

`dot`은 의미적으로 `sum(dot(vx,vy) for (vx,vy) in zip(x, y))`와 동등하지만, 인수는 동일한 길이를 가져야 한다는 추가 제한이 있습니다.

`x ⋅ y` (여기서 `⋅`는 REPL에서 `\cdot`를 탭 완성하여 입력할 수 있습니다)는 `dot(x, y)`의 동의어입니다.

# 예제

```jldoctest
julia> dot([1; 1], [2; 3])
5

julia> dot([im; im], [1; 1])
0 - 2im

julia> dot(1:5, 2:6)
70

julia> x = fill(2., (5,5));

julia> y = fill(3., (5,5));

julia> dot(x, y)
150.0
```
