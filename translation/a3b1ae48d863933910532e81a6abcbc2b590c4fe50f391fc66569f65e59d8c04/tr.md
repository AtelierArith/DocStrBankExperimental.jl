```
@doc_str -> MD
```

Verilen dizeyi Markdown metni olarak ayrıştırın, satır ve modül bilgisi ekleyin ve karşılık gelen [`MD`](@ref) nesnesini döndürün.

`@doc_str` [`Base.Docs`](@ref) modülü ile birlikte kullanılabilir. Daha fazla bilgi için lütfen [belgelendirme](@ref man-documentation) bölümüne de bakın.

# Örnekler

```
julia> s = doc"f(x) = 2*x"
  f(x) = 2*x

julia> typeof(s)
Markdown.MD

```
