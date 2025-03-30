```
Pair(x, y)
x => y
```

`Pair` nesnesini `Pair{typeof(x), typeof(y)}` türü ile oluşturun. Elemanlar `first` ve `second` alanlarında saklanır. Ayrıca yine de yineleme yoluyla erişilebilirler (ancak bir `Pair`, yayılma işlemleri için tek bir "skalar" olarak değerlendirilir).

Ayrıca bkz. [`Dict`](@ref).

# Örnekler

```jldoctest
julia> p = "foo" => 7
"foo" => 7

julia> typeof(p)
Pair{String, Int64}

julia> p.first
"foo"

julia> for x in p
           println(x)
       end
foo
7

julia> replace.(["xops", "oxps"], "x" => "o")
2-element Vector{String}:
 "oops"
 "oops"
```
