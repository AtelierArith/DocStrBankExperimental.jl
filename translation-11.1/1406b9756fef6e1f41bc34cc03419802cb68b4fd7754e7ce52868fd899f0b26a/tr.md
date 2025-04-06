```
Ref{T}
```

`T` türündeki verilere güvenli bir şekilde referans veren bir nesne. Bu tür, geçerli, Julia tarafından tahsis edilmiş doğru türdeki belleğe işaret etme garantisi verir. Temel veri, `Ref` kendisi referans edildiği sürece çöp toplayıcı tarafından serbest bırakılmaktan korunur.

Julia'da, `Ref` nesneleri `[]` ile dereferans edilir (yüklenir veya saklanır).

`T` türündeki bir `x` değerine bir `Ref` oluşturma genellikle `Ref(x)` şeklinde yazılır. Ayrıca, konteynerlere (Array veya Ptr gibi) içsel işaretçiler oluşturmak için `Ref(a, i)` şeklinde yazılabilir; bu, `a`'nın `i`-inci elemanına bir referans oluşturur.

`Ref{T}()` başlangıçsız bir `T` türündeki bir değere referans oluşturur. Bir bitstype `T` için, değer, tahsis edilen bellekte şu anda bulunan herhangi bir şey olacaktır. Bir non-bitstype `T` için, referans tanımsız olacaktır ve dereferans etmeye çalışmak "UndefRefError: tanımsız referansa erişim" hatasına yol açacaktır.

Bir `Ref`'in tanımsız bir referans olup olmadığını kontrol etmek için [`isassigned(ref::RefValue)`](@ref) kullanın. Örneğin, `isassigned(Ref{T}())` eğer `T` bir bitstype değilse `false` olacaktır. Eğer `T` bir bitstype ise, `isassigned(Ref{T}())` her zaman true olacaktır.

`ccall` argümanı olarak geçirildiğinde (ya bir `Ptr` ya da `Ref` türü olarak), bir `Ref` nesnesi, referans verdiği veriye bir yerel işaretçiye dönüştürülecektir. Çoğu `T` için veya `Ptr{Cvoid}`'a dönüştürüldüğünde, bu nesne verisine bir işaretçidir. `T` bir `isbits` türü olduğunda, bu değer güvenli bir şekilde değiştirilebilir, aksi takdirde değişiklik kesinlikle tanımsız bir davranıştır.

Özel bir durum olarak, `T = Any` olarak ayarlandığında, `Ptr{Any}`'ye dönüştürüldüğünde referansa kendisine işaret eden bir işaretçi oluşturulmasına neden olacaktır (eğer T değiştirilemezse `jl_value_t const* const*`, aksi takdirde `jl_value_t *const *`). `Ptr{Cvoid}`'a dönüştürüldüğünde, diğer `T`'ler için olduğu gibi veri bölgesine bir işaretçi döndürmeye devam edecektir.

Bir `C_NULL` örneği `ccall` `Ref` argümanına geçirilerek başlatılabilir.

# Yaygın Kullanım

`Ref`, referans verilen değerleri bir skalar olarak ele almak için bazen yaygın kullanımlarda kullanılır.

# Örnekler

```jldoctest
julia> r = Ref(5) # Başlangıç değeri ile bir Ref oluştur
Base.RefValue{Int64}(5)

julia> r[] # Bir Ref'den değer almak
5

julia> r[] = 7 # Bir Ref'de yeni bir değer saklamak
7

julia> r # Ref artık 7 içeriyor
Base.RefValue{Int64}(7)

julia> isa.(Ref([1,2,3]), [Array, Dict, Int]) # Yaygın kullanımlarda referans değerlerini skalar olarak ele al
3-element BitVector:
 1
 0
 0

julia> Ref{Function}()  # Tanımsız referans bir non-bitstype, Function
Base.RefValue{Function}(#undef)

julia> try
           Ref{Function}()[] # Tanımsız bir referansı dereferans etmek bir hataya yol açar
       catch e
           println(e)
       end
UndefRefError()

julia> Ref{Int64}()[]; # Bir bitstype'e referans verilmediğinde belirsiz bir değere işaret eder

julia> isassigned(Ref{Int64}()) # Bir bitstype'e referans her zaman atanmıştır
true
```
