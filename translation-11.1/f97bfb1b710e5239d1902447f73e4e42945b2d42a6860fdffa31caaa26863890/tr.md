```
@locals()
```

Çağrı yerinde tanımlanan tüm yerel değişkenlerin adlarını (semboller olarak) ve değerlerini içeren bir sözlük oluşturur.

!!! uyumluluk "Julia 1.1"
    Bu makro en az Julia 1.1 gerektirir.


# Örnekler

```jldoctest
julia> let x = 1, y = 2
           Base.@locals
       end
Dict{Symbol, Any} with 2 entries:
  :y => 2
  :x => 1

julia> function f(x)
           local y
           show(Base.@locals); println()
           for i = 1:1
               show(Base.@locals); println()
           end
           y = 2
           show(Base.@locals); println()
           nothing
       end;

julia> f(42)
Dict{Symbol, Any}(:x => 42)
Dict{Symbol, Any}(:i => 1, :x => 42)
Dict{Symbol, Any}(:y => 2, :x => 42)
```
