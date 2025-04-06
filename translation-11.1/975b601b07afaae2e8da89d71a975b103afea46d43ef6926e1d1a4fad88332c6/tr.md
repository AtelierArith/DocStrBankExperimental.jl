```
Base.include([mapexpr::Function,] m::Module, path::AbstractString)
```

Modül `m`'nin global kapsamındaki giriş kaynak dosyasının içeriğini değerlendirir. [`baremodule`](@ref) ile tanımlananlar hariç her modülün, o modülde dosyayı değerlendiren `m` argümanını atlayan kendi `include` tanımı vardır. Giriş dosyasının son değerlendirilen ifadesinin sonucunu döner. Dahil etme sırasında, dosyanın bulunduğu dizine göre bir görev-yerel dahil etme yolu ayarlanır. İç içe çağrılar `include`, o yola göre arama yapar. Bu işlev genellikle kaynakları etkileşimli olarak yüklemek veya birden fazla kaynak dosyasına bölünmüş paketlerde dosyaları birleştirmek için kullanılır.

İsteğe bağlı ilk argüman `mapexpr`, dahil edilen kodu değerlendirilmeye başlamadan önce dönüştürmek için kullanılabilir: `path` içindeki her bir ayrıştırılmış ifade `expr` için, `include` işlevi aslında `mapexpr(expr)`'i değerlendirir. Eğer atlanırsa, `mapexpr` varsayılan olarak [`identity`](@ref) olur.

!!! compat "Julia 1.5"
    `mapexpr` argümanını geçmek için Julia 1.5 gereklidir.

