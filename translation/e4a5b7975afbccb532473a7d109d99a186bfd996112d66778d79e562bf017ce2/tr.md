```
BoundsError([a],[i])
```

Bir diziye, `a`, yapılan bir indeksleme işlemi, `i` indeksinde bir sınır dışı öğeye erişmeye çalıştı.

# Örnekler

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> A = fill(1.0, 7);

julia> A[8]
HATA: BoundsError: 7 elemanlı Vector{Float64} dizisinde [8] indeksine erişim denemesi


julia> B = fill(1.0, (2,3));

julia> B[2, 4]
HATA: BoundsError: 2×3 Matrix{Float64} dizisinde [2, 4] indeksine erişim denemesi


julia> B[9]
HATA: BoundsError: 2×3 Matrix{Float64} dizisinde [9] indeksine erişim denemesi

```
