```
Base.datatype_alignment(dt::DataType) -> Int
```

Bu türün örnekleri için bellek tahsisatının minimum hizalamasını döndürür. Herhangi bir `isconcretetype` üzerinde çağrılabilir, ancak Bellek için, tüm nesnenin değil, elemanların hizalamasını verecektir.
