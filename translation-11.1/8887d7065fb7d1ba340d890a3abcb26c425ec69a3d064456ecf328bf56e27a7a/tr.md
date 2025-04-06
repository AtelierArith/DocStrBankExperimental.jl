```
@kwdef typedef
```

Bu, `typedef` ifadesinde belirtilen tür için otomatik olarak bir anahtar kelime tabanlı yapıcı tanımlayan bir yardımcı makrodur; bu ifade bir `struct` veya `mutable struct` ifadesi olmalıdır. Varsayılan argüman, `field::T = default` veya `field = default` biçiminde alanlar tanımlanarak sağlanır. Varsayılan bir değer sağlanmazsa, anahtar kelime argümanı, sonuçta oluşan tür yapıcısında zorunlu bir anahtar kelime argümanı haline gelir.

İç yapıcılar hala tanımlanabilir, ancak en az birinin, anahtar kelime dış yapıcı ile doğru çalışabilmesi için varsayılan iç yapıcı ile aynı biçimde (yani her alan için bir konum argümanı) argüman kabul etmesi gerekir.

!!! compat "Julia 1.1"
    Parametrik yapılar ve üst türlere sahip yapılar için `Base.@kwdef` en az Julia 1.1 gerektirir.


!!! compat "Julia 1.9"
    Bu makro, Julia 1.9 itibarıyla dışa aktarılmıştır.


# Örnekler

```jldoctest
julia> @kwdef struct Foo
           a::Int = 1         # belirtilen varsayılan
           b::String          # zorunlu anahtar kelime
       end
Foo

julia> Foo(b="hi")
Foo(1, "hi")

julia> Foo()
HATA: UndefKeywordError: anahtar kelime argümanı `b` atanmadı
Yığın izi:
[...]
```
