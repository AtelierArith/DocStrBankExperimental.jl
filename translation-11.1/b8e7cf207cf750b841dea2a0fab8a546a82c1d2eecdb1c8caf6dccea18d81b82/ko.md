```
uuid_version(u::UUID) -> Int
```

주어진 UUID를 검사하고 그 버전을 반환합니다 (자세한 내용은 [RFC 4122](https://www.ietf.org/rfc/rfc4122)를 참조하세요).

# 예제

```jldoctest
julia> uuid_version(uuid4())
4
```
