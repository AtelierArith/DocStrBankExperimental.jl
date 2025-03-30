```
Time(t::AbstractString, format::AbstractString; locale="türkçe") -> Time
```

`format` dizesinde belirtilen desene göre `t` zaman dizesini ayrıştırarak bir `Time` oluşturur (sözdizimi için [`DateFormat`](@ref) bölümüne bakın).

!!! not
    Bu yöntem her çağrıldığında bir `DateFormat` nesnesi oluşturur. Aynı formatı tekrar tekrar kullanırken performans kaybını önlemek için bunun yerine bir [`DateFormat`](@ref) nesnesi oluşturup ikinci argüman olarak kullanmanız önerilir.


# Örnekler

```jldoctest
julia> Time("12:34pm", "HH:MMp")
12:34:00

julia> a = ("12:34pm", "2:34am");

julia> [Time(d, dateformat"HH:MMp") for d ∈ a] # tercih edilen
2-element Vector{Time}:
 12:34:00
 02:34:00
```
