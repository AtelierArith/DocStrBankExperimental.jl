```
uuid_version(u::UUID) -> Int
```

Inspecte le UUID donné et retourne sa version (voir [RFC 4122](https://www.ietf.org/rfc/rfc4122)).

# Exemples

```jldoctest
julia> uuid_version(uuid4())
4
```
