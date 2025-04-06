`Text(s)`: `s`'yi düz metin olarak render eden bir nesne oluşturur.

```
Text("foo")
```

Büyük miktarda veri için bir akış da kullanabilirsiniz:

```
Text() do io
  println(io, "foo")
end
```

!!! uyarı     `Text`, geriye dönük uyumluluğu sağlamak için şu anda dışa aktarılmaktadır, ancak bu dışa aktarma artık önerilmemektedir. Bu türü [`Docs.Text`](@ref) olarak kullanmanız veya `Docs`'dan açıkça içe aktarmanız önerilir.
