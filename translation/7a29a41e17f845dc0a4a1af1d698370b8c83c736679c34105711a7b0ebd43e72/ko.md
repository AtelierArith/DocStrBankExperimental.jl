```
mean(f, itr)
```

함수 `f`를 컬렉션 `itr`의 각 요소에 적용하고 평균을 구합니다.

```jldoctest
julia> using Statistics

julia> mean(√, [1, 2, 3])
1.3820881233139908

julia> mean([√1, √2, √3])
1.3820881233139908
```
