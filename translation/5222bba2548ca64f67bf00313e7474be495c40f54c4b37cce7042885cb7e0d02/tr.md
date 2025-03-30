`HTML(s)`: `s`'yi html olarak render eden bir nesne oluşturur.

```
HTML("<div>foo</div>")
```

Büyük veri miktarları için bir akış da kullanabilirsiniz:

```
HTML() do io
  println(io, "<div>foo</div>")
end
```

!!! uyarı     `HTML`, geriye dönük uyumluluğu sağlamak için şu anda dışa aktarılmaktadır, ancak bu dışa aktarma kullanımdan kaldırılmıştır. Bu türü [`Docs.HTML`](@ref) olarak kullanmanız veya `Docs`'dan açıkça içe aktarmanız önerilir.
