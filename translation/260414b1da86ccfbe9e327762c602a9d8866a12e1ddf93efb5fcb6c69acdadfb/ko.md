```
cycle(iter[, n::Int])
```

`iter`를 영원히 순환하는 반복자입니다. `n`이 지정되면, `iter`를 그만큼 순환합니다. `iter`가 비어 있으면, `cycle(iter)`와 `cycle(iter, n)`도 비어 있습니다.

`Iterators.cycle(iter, n)`은 [`Base.repeat`](@ref)`(vector, n)`의 지연된 동등물이며, [`Iterators.repeated`](@ref)`(iter, n)`은 지연된 [`Base.fill`](@ref)`(item, n)`입니다.

!!! compat "Julia 1.11"
    `cycle(iter, n)` 메서드는 Julia 1.11에 추가되었습니다.


# 예제

```jldoctest
julia> for (i, v) in enumerate(Iterators.cycle("hello"))
           print(v)
           i > 10 && break
       end
hellohelloh

julia> foreach(print, Iterators.cycle(['j', 'u', 'l', 'i', 'a'], 3))
juliajuliajulia

julia> repeat([1,2,3], 4) == collect(Iterators.cycle([1,2,3], 4))
true

julia> fill([1,2,3], 4) == collect(Iterators.repeated([1,2,3], 4))
true
```
