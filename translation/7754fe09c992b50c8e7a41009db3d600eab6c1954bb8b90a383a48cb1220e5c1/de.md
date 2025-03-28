```
@md_str -> MD
```

Analysiere den gegebenen String als Markdown-Text und gib ein entsprechendes [`MD`](@ref) Objekt zurück.

# Beispiele

```jldoctest
julia> s = md"# Hallo, Welt!"
  Hallo, Welt!
  ≡≡≡≡≡≡≡≡≡≡≡≡≡

julia> typeof(s)
Markdown.MD

```
