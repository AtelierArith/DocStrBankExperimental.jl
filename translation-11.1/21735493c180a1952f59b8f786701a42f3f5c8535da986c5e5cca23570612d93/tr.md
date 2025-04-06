```
analyze_escapes(ir::IRCode, nargs::Int, get_escape_cache) -> estate::EscapeState
```

`ir` içindeki kaçış bilgilerini analiz eder:

  * `nargs`: analiz edilen çağrının gerçek argüman sayısı
  * `get_escape_cache(::MethodInstance) -> Union{Bool,ArgEscapeCache}`: önbelleğe alınmış argüman kaçış bilgilerini alır
