```
IOContext(io::IO, KV::Pair...)
```

Verilen bir akışı saran ve o akışın özelliklerine belirtilen `anahtar=>değer` çiftlerini ekleyen bir `IOContext` oluşturun (not: `io` kendisi bir `IOContext` olabilir).

  * Bu belirli kombinasyonun özellikler setinde olup olmadığını görmek için `(anahtar => değer) in io` kullanın.
  * Belirli bir anahtar için en son değeri almak için `get(io, anahtar, varsayılan)` kullanın.

Aşağıdaki özellikler yaygın olarak kullanılmaktadır:

  * `:compact`: Değerlerin daha kompakt bir şekilde yazdırılması gerektiğini belirten Boolean, örneğin sayıların daha az basamakla yazdırılması gerektiğini belirtir. Bu, dizi elemanları yazdırılırken ayarlanır. `:compact` çıktısı satır sonu içermemelidir.
  * `:limit`: Kapların kesilmesi gerektiğini belirten Boolean, örneğin çoğu elemanın yerinde `…` gösterilmesi.
  * `:displaysize`: Metin çıktısı için kullanılacak satır ve sütun sayısını veren bir `Tuple{Int,Int}`. Bu, çağrılan fonksiyonlar için görüntüleme boyutunu geçersiz kılmak için kullanılabilir, ancak ekran boyutunu almak için `displaysize` fonksiyonunu kullanın.
  * `:typeinfo`: Gösterilecek nesnenin türü hakkında daha önce yazdırılan bilgileri karakterize eden bir `Type`. Bu, aynı türdeki nesnelerin bir koleksiyonu gösterirken gereksiz tür bilgisinin önlenmesi için özellikle yararlıdır (örneğin, `[Float16(0)]` "Float16[0.0]" olarak gösterilebilir, "Float16[Float16(0.0)]" yerine: dizinin elemanlarını gösterirken, `:typeinfo` özelliği `Float16` olarak ayarlanacaktır).
  * `:color`: ANSI renk/kaçış kodlarının desteklenip beklenmediğini belirten Boolean. Varsayılan olarak, bu, `io`'nun uyumlu bir terminal olup olmadığına ve `julia` başlatıldığında herhangi bir `--color` komut satırı bayrağına bağlı olarak belirlenir.

# Örnekler

```jldoctest
julia> io = IOBuffer();

julia> printstyled(IOContext(io, :color => true), "string", color=:red)

julia> String(take!(io))
"\e[31mstring\e[39m"

julia> printstyled(io, "string", color=:red)

julia> String(take!(io))
"string"
```

```jldoctest
julia> print(IOContext(stdout, :compact => false), 1.12341234)
1.12341234
julia> print(IOContext(stdout, :compact => true), 1.12341234)
1.12341
```

```jldoctest
julia> function f(io::IO)
           if get(io, :short, false)
               print(io, "short")
           else
               print(io, "loooooong")
           end
       end
f (generic function with 1 method)

julia> f(stdout)
loooooong
julia> f(IOContext(stdout, :short => true))
short
```
