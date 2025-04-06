```
istextmime(m::MIME)
```

MIME 유형이 텍스트 데이터인지 여부를 결정합니다. MIME 유형은 텍스트 데이터로 알려진 특정 유형을 제외하고는 이진 데이터로 간주됩니다(가능한 유니코드 포함).

# 예제

```jldoctest
julia> istextmime(MIME("text/plain"))
true

julia> istextmime(MIME("image/png"))
false
```
