```
keys(m::RegexMatch) -> Vector
```

Tüm yakalama gruplarının anahtarlarını içeren bir vektör döndürür. Bir anahtar, yakalama grubu eşleşmeyi başaramasa bile dahil edilir. Yani, `idx` dönen değerde yer alacaktır, hatta `m[idx] == nothing` olsa bile.

İsimsiz yakalama grupları, indekslerine karşılık gelen tam sayı anahtarlarına sahip olacaktır. İsimli yakalama grupları ise string anahtarlarına sahip olacaktır.

!!! compat "Julia 1.7"
    Bu yöntem Julia 1.7'de eklendi


# Örnekler

```jldoctest
julia> keys(match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30"))
3-element Vector{Any}:
  "hour"
  "minute"
 3
```
