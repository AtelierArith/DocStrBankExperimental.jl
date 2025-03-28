```
istextmime(m::MIME)
```

Bestimmen Sie, ob ein MIME-Typ Textdaten ist. MIME-Typen werden als Binärdaten angesehen, mit Ausnahme einer Reihe von Typen, die als Textdaten bekannt sind (möglicherweise Unicode).

# Beispiele

```jldoctest
julia> istextmime(MIME("text/plain"))
true

julia> istextmime(MIME("image/png"))
false
```
