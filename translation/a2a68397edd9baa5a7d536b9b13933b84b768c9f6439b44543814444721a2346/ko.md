```
getkey(collection, key, default)
```

주어진 `key`와 일치하는 키가 `collection`에 존재하면 해당 키를 반환하고, 그렇지 않으면 `default`를 반환합니다.

# 예제

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> getkey(D, 'a', 1)
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)

julia> getkey(D, 'd', 'a')
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)
```
