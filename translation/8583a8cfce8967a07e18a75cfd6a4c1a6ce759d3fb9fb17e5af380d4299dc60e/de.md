```
merge(a::NamedTuple, iterable)
```

Interpretieren Sie ein Iterable von Schlüssel-Wert-Paaren als benanntes Tupel und führen Sie eine Zusammenführung durch.

```jldoctest
julia> merge((a=1, b=2, c=3), [:b=>4, :d=>5])
(a = 1, b = 4, c = 3, d = 5)
```
