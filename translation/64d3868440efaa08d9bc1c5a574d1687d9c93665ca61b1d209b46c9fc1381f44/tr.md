```
isleapyear(dt::TimeType) -> Bool
```

`dt`'nin yılı bir artık yıl ise `true` döner.

# Örnekler

```jldoctest
julia> isleapyear(Date("2004"))
true

julia> isleapyear(Date("2005"))
false
```
