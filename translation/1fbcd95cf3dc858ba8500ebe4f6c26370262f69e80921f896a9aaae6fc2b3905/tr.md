```
stage(ie::IndexEntry) -> Cint
```

`ie`'nin aşama numarasını alır. Aşama numarası `0`, çalışma ağacının mevcut durumunu temsil eder, ancak diğer numaralar birleştirme çatışması durumunda kullanılabilir. Bu durumda, bir `IndexEntry` üzerindeki çeşitli aşama numaraları, dosyanın mevcut durumunun hangi taraf(lar)ına ait olduğunu tanımlar. Aşama `0`, denenen birleştirmeden önceki durumu, aşama `1` ise yerel olarak yapılan değişiklikleri temsil eder, aşama `2` ve daha büyükleri ise diğer dallardan gelen değişiklikler içindir (örneğin, çoklu dal "oktopus" birleştirmesi durumunda, aşama `2`, `3` ve `4` kullanılabilir).
