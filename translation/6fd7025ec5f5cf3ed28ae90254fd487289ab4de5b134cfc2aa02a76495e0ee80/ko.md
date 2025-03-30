```
foreach(f, c...) -> Nothing
```

각 요소에 대해 함수 `f`를 호출합니다. 여러 개의 iterable 인자가 있을 경우, `f`는 요소별로 호출되며, 어떤 iterator가 끝나면 반복이 중지됩니다.

`foreach`는 `f`의 결과가 필요하지 않을 때 사용해야 합니다. 예를 들어 `foreach(println, array)`와 같이 사용합니다.

# 예제

```jldoctest
julia> tri = 1:3:7; res = Int[];

julia> foreach(x -> push!(res, x^2), tri)

julia> res
3-element Vector{Int64}:
  1
 16
 49

julia> foreach((x, y) -> println(x, " with ", y), tri, 'a':'z')
1 with a
4 with b
7 with c
```
