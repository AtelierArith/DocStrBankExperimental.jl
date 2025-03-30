```
show(io::IO, mime, x)
```

The [`display`](@ref) fonksiyonları, bir nesneyi `x` belirli bir `mime` türü olarak belirli bir I/O akışına `io` (genellikle bir bellek tamponu) yazmak için `show` çağrısında bulunur. Kullanıcı tanımlı bir tür `T` için zengin bir multimedya temsili sağlamak amacıyla, `T` için yeni bir `show` yöntemi tanımlamak yeterlidir; bu, `show(io, ::MIME"mime", x::T) = ...` şeklinde yapılır; burada `mime` bir MIME türü dizesidir ve fonksiyon gövdesi, `x`'in `io`'ya yazılacak temsili için [`write`](@ref) (veya benzeri) çağrısını içerir. (Not: `MIME""` notasyonu yalnızca literal dizeleri destekler; daha esnek bir şekilde `MIME` türleri oluşturmak için `MIME{Symbol("")}` kullanın.)

Örneğin, bir `MyImage` türü tanımlarsanız ve bunu bir PNG dosyasına yazmayı biliyorsanız, `show(io, ::MIME"image/png", x::MyImage) = ...` şeklinde bir fonksiyon tanımlayarak resimlerinizi herhangi bir PNG uyumlu `AbstractDisplay` (örneğin IJulia) üzerinde görüntülemenizi sağlayabilirsiniz. Her zamanki gibi, yerleşik Julia fonksiyonu `show`'a yeni yöntemler eklemek için `import Base.show` kullandığınızdan emin olun.

Teknik olarak, `MIME"mime"` makrosu, verilen `mime` dizesi için bir singleton türü tanımlar; bu, belirli bir türdeki nesneleri nasıl görüntüleyeceğimizi belirlemede Julia'nın dağıtım mekanizmalarından yararlanmamıza olanak tanır.

Varsayılan MIME türü `MIME"text/plain"`'dir. `text/plain` çıktısı için `show`'u 2 argümanla çağıran bir geri dönüş tanımı vardır, bu nedenle bu durum için her zaman bir yöntem eklemek gerekli değildir. Ancak bir tür, özel insan tarafından okunabilir çıktılardan faydalanıyorsa, `show(::IO, ::MIME"text/plain", ::T)` tanımlanmalıdır. Örneğin, `Day` türü `text/plain` MIME türü için `1 day` çıktısını kullanır ve `Day(1)` iki argümanlı `show`'un çıktısıdır.

# Örnekler

```jldoctest
julia> struct Day
           n::Int
       end

julia> Base.show(io::IO, ::MIME"text/plain", d::Day) = print(io, d.n, " day")

julia> Day(1)
1 day
```

Konteyner türleri genellikle `show(io, MIME"text/plain"(), x)` çağrısını yaparak 3 argümanlı `show`'u uygular; burada `x` elemanlarıdır ve ilk argüman olarak geçirilen bir [`IOContext`](@ref) içinde `:compact => true` ayarı yapılmıştır.
