```
encode(s::Union{Char,String}, encoder::AbstractEncoder)
```

Transliterate the input `String` object using a custom `encoder`. Custom `encoder` is generated using the `@transliterator`.
