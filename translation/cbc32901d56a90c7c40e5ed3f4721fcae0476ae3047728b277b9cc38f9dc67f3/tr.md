```
IdDict([itr])
```

`IdDict{K,V}()` bir hash tablosu oluşturur ve [`objectid`](@ref) hash olarak ve `===` eşitlik olarak kullanılır; anahtarlar `K` türünde ve değerler `V` türündedir. Daha fazla yardım için [`Dict`](@ref) ve bunun set versiyonu için [`IdSet`](@ref) kısmına bakın.

Aşağıdaki örnekte, `Dict` anahtarları tümü `isequal` olduğundan, aynı şekilde hashlenirler ve bu nedenle üzerine yazılırlar. `IdDict` ise nesne kimliğine göre hashler ve böylece 3 farklı anahtarı korur.

# Örnekler

```julia-repl
julia> Dict(true => "yes", 1 => "no", 1.0 => "maybe")
Dict{Real, String} with 1 entry:
  1.0 => "maybe"

julia> IdDict(true => "yes", 1 => "no", 1.0 => "maybe")
IdDict{Any, String} with 3 entries:
  true => "yes"
  1.0  => "maybe"
  1    => "no"
```
