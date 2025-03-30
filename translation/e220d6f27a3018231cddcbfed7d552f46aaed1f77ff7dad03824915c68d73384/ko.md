```
...
```

"splat" 연산자 `...`는 인수의 시퀀스를 나타냅니다. `...`는 함수 정의에서 사용되어 함수가 임의의 수의 인수를 수용할 수 있음을 나타냅니다. `...`는 또한 함수에 인수 시퀀스를 적용하는 데 사용할 수 있습니다.

# 예제

```jldoctest
julia> add(xs...) = reduce(+, xs)
add (generic function with 1 method)

julia> add(1, 2, 3, 4, 5)
15

julia> add([1, 2, 3]...)
6

julia> add(7, 1:100..., 1000:1100...)
111107
```
