```
SubstitutionString(substr) <: AbstractString
```

Verilen `substr` dizesini bir `SubstitutionString` olarak saklar, düzenli ifade yer değiştirmelerinde kullanılmak üzere. En yaygın olarak [`@s_str`](@ref) makrosu kullanılarak oluşturulur.

# Örnekler

```jldoctest
julia> SubstitutionString("Hello \\g<name>, it's \\1")
s"Hello \g<name>, it's \1"

julia> subst = s"Hello \g<name>, it's \1"
s"Hello \g<name>, it's \1"

julia> typeof(subst)
SubstitutionString{String}
```
