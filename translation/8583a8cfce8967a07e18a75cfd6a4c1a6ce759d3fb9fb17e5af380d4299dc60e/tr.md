```
merge(a::NamedTuple, iterable)
```

Bir anahtar-değer çiftleri iterable'ını adlandırılmış bir demet olarak yorumlayın ve birleştirme işlemi gerçekleştirin.

```jldoctest
julia> merge((a=1, b=2, c=3), [:b=>4, :d=>5])
(a = 1, b = 4, c = 3, d = 5)
```
