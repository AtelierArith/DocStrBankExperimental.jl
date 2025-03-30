```
enumerate(iter)
```

1부터 시작하는 카운터 `i`와 주어진 반복자에서 `i`번째 값 `x`를 포함하는 `(i, x)`를 생성하는 반복자입니다. 반복하고 있는 값 `x`뿐만 아니라 지금까지의 반복 횟수도 필요할 때 유용합니다.

`i`가 `iter`의 인덱싱에 유효하지 않거나 다른 요소를 인덱싱할 수 있습니다. 이는 `iter`의 인덱스가 1에서 시작하지 않을 때 발생하며, 문자열, 사전 등에서 발생할 수 있습니다. `i`가 인덱스가 되도록 하려면 `pairs(IndexLinear(), iter)` 메서드를 참조하세요.

# 예제

```jldoctest
julia> a = ["a", "b", "c"];

julia> for (index, value) in enumerate(a)
           println("$index $value")
       end
1 a
2 b
3 c

julia> str = "naïve";

julia> for (i, val) in enumerate(str)
           print("i = ", i, ", val = ", val, ", ")
           try @show(str[i]) catch e println(e) end
       end
i = 1, val = n, str[i] = 'n'
i = 2, val = a, str[i] = 'a'
i = 3, val = ï, str[i] = 'ï'
i = 4, val = v, StringIndexError("naïve", 4)
i = 5, val = e, str[i] = 'v'
```
