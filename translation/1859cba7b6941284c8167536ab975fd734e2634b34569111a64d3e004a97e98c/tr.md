```
styled(content::AbstractString) -> AnnotatedString
```

Biçimlendirilmiş bir dize oluşturur. Dize içinde, `{<specs>:<content>}` yapıları `<content>`'e biçimlendirme uygular; bu, virgülle ayrılmış `<specs>` spesifikasyonları listesinin gerekliliklerine göre yapılır. Her bir spesifikasyon, bir yüz adı, bir satır içi yüz spesifikasyonu veya bir `key=value` çifti biçiminde olabilir. Değer, `,=:{}` karakterlerinden herhangi birini içeriyorsa `{...}` ile sarılmalıdır.

Bu, [`@styled_str`](@ref) makrosunun işlevsel bir eşdeğeridir; sadece interpolasyon yetenekleri olmadan.
