```
setdiff!(s, itrs...)
```

집합 `s`에서 `itrs`의 각 iterable의 각 요소를 (제자리에서) 제거합니다. 배열로 순서를 유지합니다.

!!! 경고     어떤 변형된 인수가 다른 인수와 메모리를 공유할 때 동작이 예기치 않게 될 수 있습니다.

# 예시

```jldoctest
julia> a = Set([1, 3, 4, 5]);

julia> setdiff!(a, 1:2:6);

julia> a
Set{Int64} with 1 element:
  4
```
