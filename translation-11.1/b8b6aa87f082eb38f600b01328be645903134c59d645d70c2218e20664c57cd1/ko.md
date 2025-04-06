```
while
```

`while` 루프는 조건 표현식을 반복적으로 평가하며, 표현식이 참인 동안 while 루프의 본문을 계속 평가합니다. while 루프에 처음 도달했을 때 조건 표현식이 거짓이면 본문은 절대 평가되지 않습니다.

# 예제

```jldoctest
julia> i = 1
1

julia> while i < 5
           println(i)
           global i += 1
       end
1
2
3
4
```
