```
continue
```

현재 루프 반복의 나머지를 건너뜁니다.

# 예제

```jldoctest
julia> for i = 1:6
           iseven(i) && continue
           println(i)
       end
1
3
5
```
