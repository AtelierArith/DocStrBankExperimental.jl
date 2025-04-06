```
uuid_version(u::UUID) -> Int
```

Inspecciona el UUID dado y devuelve su versión (ver [RFC 4122](https://www.ietf.org/rfc/rfc4122)).

# Ejemplos

```jldoctest
julia> uuid_version(uuid4())
4
```
