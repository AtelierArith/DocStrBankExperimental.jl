```
Date(d::AbstractString, format::AbstractString; locale="türkçe") -> Date
```

`d` tarih dizesini `format` dizesinde verilen desene göre ayrıştırarak bir `Date` oluşturur (sözdizimi için [`DateFormat`](@ref) bölümüne bakın).

!!! not
    Bu yöntem her çağrıldığında bir `DateFormat` nesnesi oluşturur. Aynı formatı tekrar tekrar kullanırken performans kaybını önlemek için bunun yerine bir [`DateFormat`](@ref) nesnesi oluşturmanız ve bunu ikinci argüman olarak kullanmanız önerilir.


# Örnekler

```jldoctest
julia> Date("2020-01-01", "yyyy-mm-dd")
2020-01-01

julia> a = ("2020-01-01", "2020-01-02");

julia> [Date(d, dateformat"yyyy-mm-dd") for d ∈ a] # tercih edilen
2-element Vector{Date}:
 2020-01-01
 2020-01-02
```
