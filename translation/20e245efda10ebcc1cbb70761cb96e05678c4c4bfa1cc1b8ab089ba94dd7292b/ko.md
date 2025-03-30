```
get!(f::Union{Function, Type}, collection, key)
```

주어진 키에 대해 저장된 값을 반환하거나, 키에 대한 매핑이 없으면 `key => f()`를 저장하고 `f()`를 반환합니다.

이것은 `do` 블록 구문을 사용하여 호출되도록 설계되었습니다.

# 예제

```jldoctest
julia> squares = Dict{Int, Int}();

julia> function get_square!(d, i)
           get!(d, i) do
               i^2
           end
       end
get_square! (generic function with 1 method)

julia> get_square!(squares, 2)
4

julia> squares
Dict{Int64, Int64} with 1 entry:
  2 => 4
```
