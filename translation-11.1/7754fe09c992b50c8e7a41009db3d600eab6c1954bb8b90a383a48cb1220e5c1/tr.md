```
@md_str -> MD
```

Verilen dizeyi Markdown metni olarak ayrıştırın ve karşılık gelen [`MD`](@ref) nesnesini döndürün.

# Örnekler

```jldoctest
julia> s = md"# Merhaba, dünya!"
  Merhaba, dünya!
  ≡≡≡≡≡≡≡≡≡≡≡≡≡

julia> typeof(s)
Markdown.MD

```
