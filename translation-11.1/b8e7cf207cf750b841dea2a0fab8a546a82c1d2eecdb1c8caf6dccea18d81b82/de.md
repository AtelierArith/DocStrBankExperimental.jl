```
uuid_version(u::UUID) -> Int
```

Untersucht die gegebene UUID und gibt ihre Version zurück (siehe [RFC 4122](https://www.ietf.org/rfc/rfc4122)).

# Beispiele

```jldoctest
julia> uuid_version(uuid4())
4
```
