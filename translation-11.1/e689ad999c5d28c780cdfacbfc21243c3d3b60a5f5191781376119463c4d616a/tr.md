```
latex([io::IO], md)
```

Markdown nesnesinin `md` içeriğini LaTeX formatında çıktı olarak verir, isteğe bağlı bir `io` akışına yazabilir veya bir dize döndürebilir.

Alternatif olarak `show(io, "text/latex", md)` veya `repr("text/latex", md)` kullanılabilir.

# Örnekler

```jldoctest
julia> latex(md"hello _world_")
"hello \\emph{world}\n\n"
```
