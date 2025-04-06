`BroadcastStyle`, bir soyut tür ve nesnelerin yayılma altındaki davranışını belirlemek için kullanılan bir özellik-fonksiyondur. `BroadcastStyle(typeof(x))`, `x` ile ilişkili stili döndürür. Bir türün yayılma davranışını özelleştirmek için, bir tür/yöntem çifti tanımlayarak bir stil ilan edilebilir.

```
struct MyContainerStyle <: BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyContainer}) = MyContainerStyle()
```

Daha sonra, `Broadcasted{MyContainerStyle}` üzerinde çalışan yöntem(ler) (en az [`similar`](@ref)) yazılır. Ayrıca, yararlanabileceğiniz birkaç önceden tanımlanmış `BroadcastStyle` alt türü vardır; daha fazla bilgi için [Arayüzler bölümü](@ref man-interfaces-broadcasting)ne bakın.
