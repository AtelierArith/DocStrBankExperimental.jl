```
html([io::IO], md)
```

Markdown nesnesinin `md` içeriğini HTML formatında çıktı olarak verir, isteğe bağlı bir `io` akışına yazabilir veya bir dize döndürebilir.

Alternatif olarak `show(io, "text/html", md)` veya `repr("text/html", md)` kullanılabilir; bu yöntemler, çıktıyı `<div class="markdown"> ... </div>` öğesi içine sararak farklılık gösterir.

# Örnekler

```jldoctest
julia> html(md"hello _world_")
"<p>hello <em>world</em></p>\n"
```
