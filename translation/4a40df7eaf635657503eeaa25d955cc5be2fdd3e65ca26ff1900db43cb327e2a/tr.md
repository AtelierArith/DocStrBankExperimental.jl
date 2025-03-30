```
yieldto(t::Task, arg = nothing)
```

Verilen göreve geçiş yapar. Bir göreve ilk kez geçildiğinde, görevin fonksiyonu hiçbir argüman olmadan çağrılır. Sonraki geçişlerde, `arg` son `yieldto` çağrısından döner. Bu, yalnızca görevleri değiştiren, durumları veya zamanlamayı dikkate almayan düşük seviyeli bir çağrıdır. Kullanımı önerilmez.
