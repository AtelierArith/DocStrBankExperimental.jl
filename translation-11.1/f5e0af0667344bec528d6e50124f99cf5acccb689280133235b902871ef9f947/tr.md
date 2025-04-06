```
include([mapexpr::Function,] path::AbstractString)
```

Girdi kaynak dosyasının içeriğini içeren modülün global kapsamına değerlendirir. `baremodule` ile tanımlananlar hariç her modülün kendi `include` tanımı vardır ve bu, dosyayı o modülde değerlendirir. Girdi dosyasının son değerlendirilen ifadesinin sonucunu döner. Dahil etme sırasında, dosyanın bulunduğu dizine göre bir görev-yerel dahil etme yolu ayarlanır. İç içe çağrılar `include`, o yola göre arama yapar. Bu işlev genellikle kaynakları etkileşimli olarak yüklemek veya birden fazla kaynak dosyasına bölünmüş paketlerde dosyaları birleştirmek için kullanılır. `path` argümanı, `..` gibi göreli yol belirteçlerini çözmek ve `/`'yi uygun yol ayırıcıya dönüştürmek için [`normpath`](@ref) kullanılarak normalize edilir.

İsteğe bağlı ilk argüman `mapexpr`, dahil edilen kodu değerlendirilmeye başlamadan önce dönüştürmek için kullanılabilir: `path` içindeki her ayrıştırılmış ifade `expr` için, `include` işlevi aslında `mapexpr(expr)`'i değerlendirir. Eğer atlanırsa, `mapexpr` varsayılan olarak [`identity`](@ref) olur.

Başka bir modüle bir dosyayı değerlendirmek için [`Base.include`](@ref) kullanın.

!!! compat "Julia 1.5"
    `mapexpr` argümanını geçmek için Julia 1.5 gereklidir.

