```
isreal(x) -> Bool
```

`x` veya tüm elemanlarının sonsuzluklar ve NaN'lar dahil olmak üzere bazı reel sayılara sayısal olarak eşit olup olmadığını test eder. `isreal(x)` eğer `isequal(x, real(x))` doğruysa doğrudur.

# Örnekler

```jldoctest
julia> isreal(5.)
true

julia> isreal(1 - 3im)
false

julia> isreal(Inf + 0im)
true

julia> isreal([4.; complex(0,1)])
false
```
