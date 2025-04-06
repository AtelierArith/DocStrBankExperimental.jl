```
include_string([mapexpr::Function,] m::Module, code::AbstractString, filename::AbstractString="string")
```

[`include`](@ref) ile benzer, ancak kodu bir dosyadan değil, verilen string'den okur.

İsteğe bağlı ilk argüman `mapexpr`, dahil edilen kodu değerlendirilmeye başlamadan önce dönüştürmek için kullanılabilir: `code` içindeki her bir ayrıştırılmış ifade `expr` için, `include_string` fonksiyonu aslında `mapexpr(expr)`'i değerlendirir. Eğer belirtilmezse, `mapexpr` varsayılan olarak [`identity`](@ref) olur.

!!! compat "Julia 1.5"
    `mapexpr` argümanını geçmek için Julia 1.5 gereklidir.

