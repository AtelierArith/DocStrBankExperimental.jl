```
uuid_version(u::UUID) -> Int
```

Verilen UUID'yi inceler ve versiyonunu döndürür (bkz. [RFC 4122](https://www.ietf.org/rfc/rfc4122)).

# Örnekler

```jldoctest
julia> uuid_version(uuid4())
4
```
