```
propertynames(x, private=false)
```

Bir nesnenin (`x.property`) özelliklerinin bir demetini veya vektörünü alır. Bu genellikle [`fieldnames(typeof(x))`](@ref) ile aynıdır, ancak [`getproperty`](@ref) ile aşırı yükleme yapan türlerin, türün bir örneğinin özelliklerini almak için genellikle `propertynames`'i de aşırı yüklemesi gerekir.

`propertynames(x)` yalnızca `x`'in belgelenmiş arayüzünün bir parçası olan "genel" özellik adlarını döndürebilir. İç kullanım için tasarlanmış "özel" özellik adlarını da döndürmesini istiyorsanız, isteğe bağlı ikinci argüman için `true` geçin. REPL sekme tamamlama `x.` üzerinde yalnızca `private=false` özelliklerini gösterir.

Ayrıca bakınız: [`hasproperty`](@ref), [`hasfield`](@ref).
