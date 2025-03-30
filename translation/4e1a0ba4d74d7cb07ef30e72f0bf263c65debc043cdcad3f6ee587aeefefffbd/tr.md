```
ntuple(f, n::Integer)
```

`n` uzunluğunda bir demet oluşturur, her bir öğeyi `f(i)` olarak hesaplar; burada `i` öğenin indeksidir.

# Örnekler

```jldoctest
julia> ntuple(i -> 2*i, 4)
(2, 4, 6, 8)
```
