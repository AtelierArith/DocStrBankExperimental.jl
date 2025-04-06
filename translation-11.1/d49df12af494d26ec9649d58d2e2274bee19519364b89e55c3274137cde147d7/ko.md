```
countfrom(start=1, step=1)
```

시작 `start`에서 시작하여 `step`만큼 증가하는 무한 카운트 이터레이터입니다.

# 예제

```jldoctest
julia> for v in Iterators.countfrom(5, 2)
           v > 10 && break
           println(v)
       end
5
7
9
```
