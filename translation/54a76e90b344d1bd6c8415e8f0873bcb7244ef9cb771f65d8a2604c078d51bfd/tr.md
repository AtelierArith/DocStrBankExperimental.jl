```
print([to_toml::Function], io::IO [=stdout], data::AbstractDict; sorted=false, by=identity, inline_tables::IdSet{<:AbstractDict})
```

`data`'yı `io` akışına TOML sözdizimi olarak yazın. Eğer `sorted` anahtar argümanı `true` olarak ayarlandıysa, tablolar `by` anahtar argümanı ile verilen fonksiyona göre sıralanmalıdır. Eğer `inline_tables` anahtar argümanı verilmişse, "inline" olarak yazdırılması gereken tabloların bir kümesi olmalıdır.

Aşağıdaki veri türleri desteklenmektedir: `AbstractDict`, `AbstractVector`, `AbstractString`, `Integer`, `AbstractFloat`, `Bool`, `Dates.DateTime`, `Dates.Time`, `Dates.Date`. Tam sayılar ve ondalık sayılar sırasıyla `Float64` ve `Int64`'e dönüştürülebilir olmalıdır. Diğer veri türleri için, veri türlerini alıp desteklenen bir türde bir değer döndüren `to_toml` fonksiyonunu geçirin.
