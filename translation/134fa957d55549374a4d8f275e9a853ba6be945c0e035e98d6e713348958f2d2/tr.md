```
RegexMatch <: AbstractMatch
```

Bir dize içinde bulunan bir [`Regex`](@ref) için tek bir eşleşmeyi temsil eden bir türdür. Genellikle [`match`](@ref) fonksiyonundan oluşturulur.

`match` alanı, tüm eşleşen dize parçasını saklar. `captures` alanı, her bir yakalama grubu için numara ile indekslenmiş alt dizeleri saklar. Yakalama grubu adı ile indekslemek için, tüm eşleşme nesnesi bunun yerine indekslenmelidir; örneklerde gösterildiği gibi. Eşleşmenin başlangıç konumu `offset` alanında saklanır. `offsets` alanı, her yakalama grubunun başlangıç konumlarını saklar; 0, yakalanmamış bir grubu belirtir.

Bu tür, `Regex`'in yakalama grupları üzerinde bir yineleyici olarak kullanılabilir ve her grupta yakalanan alt dizeleri verir. Bu nedenle, bir eşleşmenin yakalamaları parçalanabilir. Eğer bir grup yakalanmamışsa, bir alt dize yerine `nothing` dönecektir.

`RegexMatch` nesnesini kabul eden yöntemler [`iterate`](@ref), [`length`](@ref), [`eltype`](@ref), [`keys`](@ref keys(::RegexMatch)), [`haskey`](@ref) ve [`getindex`](@ref) için tanımlanmıştır; burada anahtarlar bir yakalama grubunun adları veya numaralarıdır. Daha fazla bilgi için [`keys`](@ref keys(::RegexMatch))'e bakın.

# Örnekler

```jldoctest
julia> m = match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30 in the morning")
RegexMatch("11:30", hour="11", minute="30", 3=nothing)

julia> m.match
"11:30"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "11"
 "30"
 nothing


julia> m["minute"]
"30"

julia> hr, min, ampm = m; # yakalama gruplarını yineleme ile parçala

julia> hr
"11"
```
