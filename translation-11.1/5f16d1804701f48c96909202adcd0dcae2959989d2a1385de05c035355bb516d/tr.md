```
DateTime(dt::AbstractString, format::AbstractString; locale="english") -> DateTime
```

`dt` tarih saat dizesini `format` dizesinde verilen desene göre ayrıştırarak bir `DateTime` oluşturur (sözdizimi için [`DateFormat`](@ref) bakınız).

!!! not
    Bu yöntem her çağrıldığında bir `DateFormat` nesnesi oluşturur. Aynı formatı tekrar tekrar kullanırken performans kaybını önlemek için bunun yerine bir [`DateFormat`](@ref) nesnesi oluşturmanız ve bunu ikinci argüman olarak kullanmanız önerilir.


# Örnekler

```jldoctest
julia> DateTime("2020-01-01", "yyyy-mm-dd")
2020-01-01T00:00:00

julia> a = ("2020-01-01", "2020-01-02");

julia> [DateTime(d, dateformat"yyyy-mm-dd") for d ∈ a] # tercih edilen
2-element Vector{DateTime}:
 2020-01-01T00:00:00
 2020-01-02T00:00:00
```
