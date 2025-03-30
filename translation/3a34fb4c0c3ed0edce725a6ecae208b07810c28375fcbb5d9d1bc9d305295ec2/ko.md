```
flatten(iter)
```

주어진 반복자가 반복자를 생성하는 경우, 해당 반복자의 요소를 생성하는 반복자를 반환합니다. 다시 말해, 인수 반복자의 요소가 연결됩니다.

# 예제

```jldoctest
julia> collect(Iterators.flatten((1:2, 8:9)))
4-element Vector{Int64}:
 1
 2
 8
 9

julia> [(x,y) for x in 0:1 for y in 'a':'c']  # Iterators.flatten을 포함하는 생성기를 수집합니다.
6-element Vector{Tuple{Int64, Char}}:
 (0, 'a')
 (0, 'b')
 (0, 'c')
 (1, 'a')
 (1, 'b')
 (1, 'c')
```
