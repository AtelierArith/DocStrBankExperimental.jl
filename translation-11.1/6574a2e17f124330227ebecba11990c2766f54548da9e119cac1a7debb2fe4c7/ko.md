```
break
```

루프에서 즉시 빠져나옵니다.

# 예제

```jldoctest
julia> i = 0
0

julia> while true
           global i += 1
           i > 5 && break
           println(i)
       end
1
2
3
4
5
```
