```
Base.datatype_haspadding(dt::DataType) -> Bool
```

Bu türün örneklerinin alanlarının bellekte, arada hiçbir dolgu biti olmadan paketlenip paketlenmediğini döndürür (dolgu bitleri, yapı alanlarına uygulandığında eşitlik testini benzersiz bir şekilde etkilemeyen bitler olarak tanımlanır). Herhangi bir `isconcretetype` üzerinde çağrılabilir.
