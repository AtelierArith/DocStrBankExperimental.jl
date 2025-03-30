```
foldl(op, itr; [init])
```

[`reduce`](@ref)와 유사하지만 왼쪽 결합성이 보장됩니다. 제공된 경우, 키워드 인수 `init`은 정확히 한 번 사용됩니다. 일반적으로 빈 컬렉션과 작업하기 위해 `init`을 제공해야 합니다.

또한 [`mapfoldl`](@ref), [`foldr`](@ref), [`accumulate`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> foldl(=>, 1:4)
((1 => 2) => 3) => 4

julia> foldl(=>, 1:4; init=0)
(((0 => 1) => 2) => 3) => 4

julia> accumulate(=>, (1,2,3,4))
(1, 1 => 2, (1 => 2) => 3, ((1 => 2) => 3) => 4)
```
