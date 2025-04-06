```
promote_type(type1, type2, ...)
```

Promosyon, karışık türlerin değerlerini tek bir ortak türe dönüştürmeyi ifade eder. `promote_type`, operatörler (genellikle matematiksel) farklı türlerde argümanlar aldığında Julia'daki varsayılan promosyon davranışını temsil eder. `promote_type` genellikle, aşırı genişletme olmadan, her iki giriş türünün çoğu değerini en azından yaklaşık olarak temsil edebilecek bir tür döndürmeye çalışır. Bazı kayıplara tolerans gösterilir; örneğin, `promote_type(Int64, Float64)` [`Float64`](@ref) döndürür, oysa ki katı olarak, tüm [`Int64`](@ref) değerleri tam olarak `Float64` değerleri olarak temsil edilemez.

Ayrıca bakınız: [`promote`](@ref), [`promote_typejoin`](@ref), [`promote_rule`](@ref).

# Örnekler

```jldoctest
julia> promote_type(Int64, Float64)
Float64

julia> promote_type(Int32, Int64)
Int64

julia> promote_type(Float32, BigInt)
BigFloat

julia> promote_type(Int16, Float16)
Float16

julia> promote_type(Int64, Float16)
Float16

julia> promote_type(Int8, UInt16)
UInt16
```

!!! uyarı "Bunu doğrudan aşırı yüklemeyin"     Kendi türleriniz için promosyonu aşırı yüklemek istiyorsanız, [`promote_rule`](@ref) aşırı yüklemelisiniz. `promote_type`, türü belirlemek için dahili olarak `promote_rule`'ü çağırır. `promote_type`'ı doğrudan aşırı yüklemek belirsizlik hatalarına neden olabilir.
