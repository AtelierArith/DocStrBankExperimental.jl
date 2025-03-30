# Calling C and Fortran Code

Çoğu kod Julia'da yazılabilse de, C ve Fortran'da zaten yazılmış birçok yüksek kaliteli, olgun kütüphane bulunmaktadır. Mevcut bu kodların kolayca kullanılabilmesi için, Julia C ve Fortran fonksiyonlarını çağırmayı basit ve verimli hale getirir. Julia'nın "boş kod yok" felsefesi vardır: fonksiyonlar, herhangi bir "bağlantı" kodu, kod üretimi veya derleme olmadan, doğrudan Julia'dan çağrılabilir - hatta etkileşimli istemciden bile. Bu, uygun bir çağrı yaparak [`@ccall`](@ref) makrosu (veya daha az kullanışlı [`ccall`](@ref) sözdizimi, bkz. [`ccall` syntax section](@ref ccall-interface) ) ile gerçekleştirilir.

Çağrılacak kodun bir paylaşılan kütüphane olarak mevcut olması gerekir. Çoğu C ve Fortran kütüphanesi zaten paylaşılan kütüphaneler olarak derlenmiş olarak gelir, ancak kodu kendiniz GCC (veya Clang) kullanarak derliyorsanız, `-shared` ve `-fPIC` seçeneklerini kullanmanız gerekecektir. Julia'nın JIT tarafından üretilen makine talimatları, yerel bir C çağrısınınkilerle aynıdır, bu nedenle sonuçta oluşan ek yük, C kodundan bir kütüphane işlevini çağırmakla aynıdır. [^1]

Varsayılan olarak, Fortran derleyicileri [generate mangled names](https://en.wikipedia.org/wiki/Name_mangling#Fortran) (örneğin, fonksiyon adlarını küçük harfe veya büyük harfe dönüştürmek, genellikle bir alt çizgi eklemek) kullanır ve bu nedenle bir Fortran fonksiyonunu çağırmak için, Fortran derleyicinizin izlediği kurala karşılık gelen mangled tanımlayıcıyı geçirmeniz gerekir. Ayrıca, bir Fortran fonksiyonu çağırırken, tüm girdilerin yığın veya yığın üzerinde tahsis edilmiş değerlere işaretçi olarak geçirilmesi gerekir. Bu, genellikle yığın üzerinde tahsis edilen diziler ve diğer değiştirilebilir nesneler için geçerli olduğu gibi, genellikle yığın üzerinde tahsis edilen ve C veya Julia çağrı sözleşmeleri kullanıldığında genellikle kayıtlarda geçirilen tam sayılar ve float gibi skalar değerler için de geçerlidir.

[`@ccall`](@ref) kütüphane fonksiyonuna çağrı yapmak için sözdizimi:

```julia
  @ccall library.function_name(argvalue1::argtype1, ...)::returntype
  @ccall function_name(argvalue1::argtype1, ...)::returntype
  @ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

`library` bir dize sabiti veya literaldir (ancak aşağıdaki [Non-constant Function Specifications](@ref) kısmına bakın). Kütüphane atlanabilir; bu durumda, işlev adı mevcut süreçte çözülür. Bu form, C kütüphane işlevlerini, Julia çalışma zamanındaki işlevleri veya Julia ile bağlantılı bir uygulamadaki işlevleri çağırmak için kullanılabilir. Kütüphaneye tam yol da belirtilebilir. Alternatif olarak, `@ccall` bir işlev işaretçisi `$function_pointer` çağırmak için de kullanılabilir; bu, `Libdl.dlsym` tarafından döndürülen bir işlev işaretçisidir. `argtype`'lar C işlev imzasına karşılık gelir ve `argvalue`'lar işleve iletilmesi gereken gerçek argüman değerleridir.

!!! note
    Aşağıda [map C types to Julia types](@ref mapping-c-types-to-julia) nasıl yapılacağına dair bilgi bulabilirsiniz.


Tam bir ama basit bir örnek olarak, aşağıdaki kod, çoğu Unix türevi sistemde standart C kütüphanesinden `clock` fonksiyonunu çağırır:

```julia-repl
julia> t = @ccall clock()::Int32
2292761

julia> typeof(t)
Int32
```

`clock` hiçbir argüman almaz ve bir `Int32` döner. Bir ortam değişkeninin değerine işaretçi almak için `getenv` fonksiyonu çağrıldığında, şöyle bir çağrı yapılır:

```julia-repl
julia> path = @ccall getenv("SHELL"::Cstring)::Cstring
Cstring(@0x00007fff5fbffc45)

julia> unsafe_string(path)
"/bin/bash"
```

Pratikte, özellikle yeniden kullanılabilir işlevsellik sağlarken, genellikle `@ccall` kullanımlarını, argümanları ayarlayan ve ardından C veya Fortran işlevinin belirttiği şekilde hataları kontrol eden Julia işlevlerine sararız. Ve bir hata meydana gelirse, bu normal bir Julia istisnası olarak fırlatılır. Bu, C ve Fortran API'lerinin hata koşullarını belirtme konusunda tutarsız olmaları nedeniyle özellikle önemlidir. Örneğin, `getenv` C kütüphane işlevi, aşağıdaki Julia işlevinde sarılmıştır; bu, [`env.jl`](https://github.com/JuliaLang/julia/blob/master/base/env.jl)'den alınmış basitleştirilmiş bir versiyondur:

```julia
function getenv(var::AbstractString)
    val = @ccall getenv(var::Cstring)::Cstring
    if val == C_NULL
        error("getenv: undefined variable: ", var)
    end
    return unsafe_string(val)
end
```

C `getenv` fonksiyonu bir hatayı `C_NULL` döndürerek belirtir, ancak diğer standart C fonksiyonları hataları farklı şekillerde belirtir; bunlar arasında -1, 0, 1 ve diğer özel değerler bulunur. Bu sarmalayıcı, çağıran kişi var olmayan bir ortam değişkenini almaya çalışırsa sorunu belirten bir istisna fırlatır:

```julia-repl
julia> getenv("SHELL")
"/bin/bash"

julia> getenv("FOOBAR")
ERROR: getenv: undefined variable: FOOBAR
```

İşte yerel makinenin ana bilgisayar adını keşfeden biraz daha karmaşık bir örnek.

```julia
function gethostname()
    hostname = Vector{UInt8}(undef, 256) # MAXHOSTNAMELEN
    err = @ccall gethostname(hostname::Ptr{UInt8}, sizeof(hostname)::Csize_t)::Int32
    Base.systemerror("gethostname", err != 0)
    hostname[end] = 0 # ensure null-termination
    return GC.@preserve hostname unsafe_string(pointer(hostname))
end
```

Bu örnek önce bir bayt dizisi ayırır. Ardından, diziyi ana bilgisayar adıyla doldurmak için C kütüphane fonksiyonu `gethostname`'i çağırır. Son olarak, ana bilgisayar adı tamponuna bir işaretçi alır ve işaretçiyi, null ile sonlandırılmış bir C dizesi olduğunu varsayarak bir Julia dizesine dönüştürür.

C kütüphanelerinin, çağıranın çağrılan tarafa iletilmek üzere bellek ayırmasını gerektiren bu deseni kullanması yaygındır. Julia'dan bu şekilde bellek ayırma genellikle başlatılmamış bir dizi oluşturarak ve verilerine bir işaretçi geçirerek C fonksiyonuna iletilerek gerçekleştirilir. Bu nedenle burada `Cstring` türünü kullanmıyoruz: dizi başlatılmamış olduğundan, null baytlar içerebilir. `@ccall` ile `Cstring`'e dönüştürme, içerdiği null baytları kontrol eder ve bu nedenle bir dönüştürme hatası fırlatabilir.

`pointer(hostname)`'in `unsafe_string` ile dereferans alması, `hostname` için ayrılan belleğe erişim gerektirdiğinden tehlikeli bir işlemdir; bu bellek, o arada çöp toplayıcı tarafından temizlenmiş olabilir. [`GC.@preserve`](@ref) makrosu bunun olmasını engeller ve dolayısıyla geçersiz bir bellek konumuna erişimi önler.

Sonunda, bir yolu belirterek bir kütüphane örneği burada. Aşağıdaki içeriğe sahip bir paylaşılan kütüphane oluşturuyoruz.

```c
#include <stdio.h>

void say_y(int y)
{
    printf("Hello from C: got y = %d.\n", y);
}
```

ve `gcc -fPIC -shared -o mylib.so mylib.c` ile derleyin. Daha sonra, kütüphane adı olarak (mutlak) yolu belirterek çağrılabilir:

```julia-repl
julia> @ccall "./mylib.so".say_y(5::Cint)::Cvoid
Hello from C: got y = 5.
```

## Creating C-Compatible Julia Function Pointers

Julia fonksiyonlarını, işlev işaretçisi argümanlarını kabul eden yerel C fonksiyonlarına geçirmek mümkündür. Örneğin, aşağıdaki gibi C prototipleriyle eşleşmek için:

```c
typedef returntype (*functiontype)(argumenttype, ...)
```

Makro [`@cfunction`](@ref), bir Julia fonksiyonuna yapılan çağrı için C uyumlu fonksiyon işaretçisini oluşturur. `4d61726b646f776e2e436f64652822222c2022406366756e6374696f6e2229_40726566`'ya verilen argümanlar şunlardır:

1. Bir Julia fonksiyonu
2. Fonksiyonun dönüş tipi
3. Bir işlev imzasına karşılık gelen giriş türlerinin bir demeti

!!! note
    `@ccall` ile birlikte, dönüş türü ve girdi türleri, literal sabitler olmalıdır.


!!! note
    Şu anda yalnızca platforma varsayılan C çağrı sözleşmesi desteklenmektedir. Bu, `@cfunction` ile oluşturulan işaretçilerin, 32-bit Windows'ta WINAPI'nin `stdcall` bir işlev beklediği çağrılarda kullanılamayacağı, ancak WIN64'te (burada `stdcall` C çağrı sözleşmesi ile birleştirilmiştir) kullanılabileceği anlamına gelir.


!!! note
    `@cfunction` ile açığa çıkarılan geri çağırma fonksiyonları hata fırlatmamalıdır, çünkü bu, kontrolü beklenmedik bir şekilde Julia çalışma zamanına geri döndürecek ve programı tanımsız bir durumda bırakabilir.


Klasik bir örnek, şu şekilde bildirilen standart C kütüphanesi `qsort` fonksiyonudur:

```c
void qsort(void *base, size_t nitems, size_t size,
           int (*compare)(const void*, const void*));
```

`base` argümanı, her biri `size` byte olan `nitems` uzunluğunda bir diziye işaret eden bir işaretçidir. `compare`, iki eleman `a` ve `b` için işaretçiler alan ve `a`nın `b`den önce/sonra görünmesi gerektiğinde sıfırdan küçük/büyük bir tamsayı döndüren bir geri çağırma fonksiyonudur (veya herhangi bir sıralamanın izin verildiği durumlarda sıfır döner).

Şimdi, Julia'da `qsort` fonksiyonunu kullanarak sıralamak istediğimiz `A` değerlerinden oluşan 1 boyutlu bir diziye sahip olduğumuzu varsayalım (Julia'nın yerleşik `sort` fonksiyonu yerine). `qsort`'ı çağırmadan ve argümanları geçmeden önce, bir karşılaştırma fonksiyonu yazmamız gerekiyor:

```jldoctest mycompare
julia> function mycompare(a, b)::Cint
           return (a < b) ? -1 : ((a > b) ? +1 : 0)
       end;
```

`qsort`, bir karşılaştırma fonksiyonu bekler ve bu fonksiyon bir C `int` döndürmelidir, bu nedenle dönüş türünü `Cint` olarak belirtiriz.

Bu fonksiyonu C'ye geçirmek için, adresini `@cfunction` makrosunu kullanarak alırız:

```jldoctest mycompare
julia> mycompare_c = @cfunction(mycompare, Cint, (Ref{Cdouble}, Ref{Cdouble}));
```

[`@cfunction`](@ref) üç argüman gerektirir: Julia fonksiyonu (`mycompare`), dönüş türü (`Cint`) ve girdi argüman türlerinin literal demeti, bu durumda bir `Cdouble` ([`Float64`](@ref)) dizisini sıralamak için.

Son çağrı `qsort` şöyle görünüyor:

```jldoctest mycompare
julia> A = [1.3, -2.7, 4.4, 3.1];

julia> @ccall qsort(A::Ptr{Cdouble}, length(A)::Csize_t, sizeof(eltype(A))::Csize_t, mycompare_c::Ptr{Cvoid})::Cvoid

julia> A
4-element Vector{Float64}:
 -2.7
  1.3
  3.1
  4.4
```

Örnek gösterdiği gibi, orijinal Julia dizisi `A` artık sıralanmış durumda: `[-2.7, 1.3, 3.1, 4.4]`. Julia'nın [takes care of converting the array to a `Ptr{Cdouble}`](@ref automatic-type-conversion)), eleman tipinin boyutunu bayt cinsinden hesaplama gibi işlemler yapmaktadır.

Eğlence için, `mycompare` içine bir `println("mycompare($a, $b)")` satırı eklemeyi deneyin; bu, `qsort`'un gerçekleştirdiği karşılaştırmaları görmenizi sağlayacak (ve gerçekten ona geçirdiğiniz Julia fonksiyonunu çağırdığını doğrulamak için).

## [Mapping C Types to Julia](@id mapping-c-types-to-julia)

C türünün Julia'daki bildirimiyle tam olarak eşleşmesi kritik öneme sahiptir. Tutarsızlıklar, bir sistemde doğru çalışan kodun başka bir sistemde başarısız olmasına veya belirsiz sonuçlar üretmesine neden olabilir.

Not edin ki, C fonksiyonlarını çağırma sürecinde hiçbir C başlık dosyası kullanılmamaktadır: Julia türlerinizin ve çağrı imzalarınızın C başlık dosyasındaki türleri ve imzaları doğru bir şekilde yansıttığından siz sorumlusunuz.[^2]

### [Automatic Type Conversion](@id automatic-type-conversion)

Julia otomatik olarak her argümanı belirtilen türe dönüştürmek için [`Base.cconvert`](@ref) fonksiyonuna çağrılar ekler. Örneğin, aşağıdaki çağrı:

```julia
@ccall "libfoo".foo(x::Int32, y::Float64)::Cvoid
```

bunu yazılmış gibi davranacaktır:

```julia
c_x = Base.cconvert(Int32, x)
c_y = Base.cconvert(Float64, y)
GC.@preserve c_x c_y begin
    @ccall "libfoo".foo(
        Base.unsafe_convert(Int32, c_x)::Int32,
        Base.unsafe_convert(Float64, c_y)::Float64
    )::Cvoid
end
```

[`Base.cconvert`](@ref) normalde [`convert`](@ref) çağrısını yapar, ancak C'ye geçmek için daha uygun olan keyfi yeni bir nesne döndürmek üzere tanımlanabilir. Bu, C kodu tarafından erişilecek tüm bellek tahsisatlarını gerçekleştirmek için kullanılmalıdır. Örneğin, bu, nesnelerin (örneğin, dizelerin) bir `Array`'ini işaretçi dizisine dönüştürmek için kullanılır.

[`Base.unsafe_convert`](@ref) türlerini [`Ptr`](@ref) türlerine dönüştürür. Bir nesneyi yerel bir işaretçiye dönüştürmek, nesneyi çöp toplayıcıdan gizleyebileceği için güvensiz olarak kabul edilir ve bu da nesnenin erken serbest bırakılmasına neden olabilir.

### Type Correspondences

Öncelikle, bazı ilgili Julia tür terminolojisini gözden geçirelim:

| Syntax / Keyword        | Example                                    | Description                                                                                                                                                                                                                                                       |
|:----------------------- |:------------------------------------------ |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mutable struct`        | `BitSet`                                   | "Leaf Type" :: A group of related data that includes a type-tag, is managed by the Julia GC, and is defined by object-identity. The type parameters of a leaf type must be fully defined (no `TypeVars` are allowed) in order for the instance to be constructed. |
| `abstract type`         | `Any`, `AbstractArray{T, N}`, `Complex{T}` | "Super Type" :: A super-type (not a leaf-type) that cannot be instantiated, but can be used to describe a group of types.                                                                                                                                         |
| `T{A}`                  | `Vector{Int}`                              | "Type Parameter" :: A specialization of a type (typically used for dispatch or storage optimization).                                                                                                                                                             |
|                         |                                            | "TypeVar" :: The `T` in the type parameter declaration is referred to as a TypeVar (short for type variable).                                                                                                                                                     |
| `primitive type`        | `Int`, `Float64`                           | "Primitive Type" :: A type with no fields, but a size. It is stored and defined by-value.                                                                                                                                                                         |
| `struct`                | `Pair{Int, Int}`                           | "Struct" :: A type with all fields defined to be constant. It is defined by-value, and may be stored with a type-tag.                                                                                                                                             |
|                         | `ComplexF64` (`isbits`)                    | "Is-Bits"   :: A `primitive type`, or a `struct` type where all fields are other `isbits` types. It is defined by-value, and is stored without a type-tag.                                                                                                        |
| `struct ...; end`       | `nothing`                                  | "Singleton" :: a Leaf Type or Struct with no fields.                                                                                                                                                                                                              |
| `(...)` or `tuple(...)` | `(1, 2, 3)`                                | "Tuple" :: an immutable data-structure similar to an anonymous struct type, or a constant array. Represented as either an array or a struct.                                                                                                                      |

### [Bits Types](@id man-bits-types)

Bilinmesi gereken birkaç özel tür vardır, çünkü başka hiçbir tür aynı şekilde davranacak şekilde tanımlanamaz:

  * `Float32`

    Tam olarak C'deki `float` türüne (veya Fortran'daki `REAL*4`'e) karşılık gelir.
  * `Float64`

    Tam olarak C'deki `double` türüne (veya Fortran'daki `REAL*8`'e) karşılık gelir.
  * `KarmaşıkF32`

    Tam olarak C'deki `complex float` türüne (veya Fortran'daki `COMPLEX*8`'e) karşılık gelir.
  * `KarmaşıkF64`

    Tam olarak C'deki `complex double` türüne (veya Fortran'daki `COMPLEX*16`'ya) karşılık gelir.
  * `İmzalı`

    Tam olarak C'deki `signed` türü anotasyonuna (veya Fortran'daki herhangi bir `INTEGER` türüne) karşılık gelir. [`Signed`](@ref) alt türü olmayan herhangi bir Julia türü, işaretsiz olarak varsayılır.

  * `Ref{T}`

    `Ptr{T}` gibi davranır ve belleğini Julia GC aracılığıyla yönetebilir.

  * `Dizi{T,N}`

    Bir dizi C'ye `Ptr{T}` argümanı olarak geçirildiğinde, yeniden yorumlama yapılmaz: Julia, dizinin eleman türünün `T` ile eşleşmesini gerektirir ve ilk elemanın adresi geçirilir.

    Bu nedenle, bir `Array` yanlış formatta veri içeriyorsa, `trunc.(Int32, A)` gibi bir çağrı kullanılarak açıkça dönüştürülmesi gerekecektir.

    Bir diziyi `A` farklı bir türün işaretçisi olarak *önceden veri dönüştürmeden* (örneğin, bir `Float64` dizisini yorumlanmamış baytlar üzerinde çalışan bir işleve geçirmek için) geçirmek için, argümanı `Ptr{Cvoid}` olarak tanımlayabilirsiniz.

    Eğer `Ptr{T}` türünde bir dizi `Ptr{Ptr{T}}` argümanı olarak geçilirse, [`Base.cconvert`](@ref) dizinin her bir elemanının `4d61726b646f776e2e436f64652822222c2022426173652e63636f6e766572742229_40726566` versiyonu ile değiştirildiği null-terminatörlü bir kopyasını ilk olarak yapmaya çalışacaktır. Bu, örneğin, `Vector{String}` türünde bir `argv` işaretçi dizisini `Ptr{Ptr{Cchar}}` türündeki bir argümana geçirmeye olanak tanır.

Tüm desteklediğimiz sistemlerde, temel C/C++ değer türleri Julia türlerine aşağıdaki gibi çevrilebilir. Her C türünün, aynı isimle, C ile ön eklenmiş bir karşılık Julia türü vardır. Bu, taşınabilir kod yazarken yardımcı olabilir (ve C'deki bir `int`'in Julia'daki bir `Int` ile aynı olmadığını hatırlamak).

**Sistem Bağımsız Türler**

| C name                                                  | Fortran name             | Standard Julia Alias | Julia Base Type                                                                                             |
|:------------------------------------------------------- |:------------------------ |:-------------------- |:----------------------------------------------------------------------------------------------------------- |
| `unsigned char`                                         | `CHARACTER`              | `Cuchar`             | `UInt8`                                                                                                     |
| `bool` (_Bool in C99+)                                  |                          | `Cuchar`             | `UInt8`                                                                                                     |
| `short`                                                 | `INTEGER*2`, `LOGICAL*2` | `Cshort`             | `Int16`                                                                                                     |
| `unsigned short`                                        |                          | `Cushort`            | `UInt16`                                                                                                    |
| `int`, `BOOL` (C, typical)                              | `INTEGER*4`, `LOGICAL*4` | `Cint`               | `Int32`                                                                                                     |
| `unsigned int`                                          |                          | `Cuint`              | `UInt32`                                                                                                    |
| `long long`                                             | `INTEGER*8`, `LOGICAL*8` | `Clonglong`          | `Int64`                                                                                                     |
| `unsigned long long`                                    |                          | `Culonglong`         | `UInt64`                                                                                                    |
| `intmax_t`                                              |                          | `Cintmax_t`          | `Int64`                                                                                                     |
| `uintmax_t`                                             |                          | `Cuintmax_t`         | `UInt64`                                                                                                    |
| `float`                                                 | `REAL*4i`                | `Cfloat`             | `Float32`                                                                                                   |
| `double`                                                | `REAL*8`                 | `Cdouble`            | `Float64`                                                                                                   |
| `complex float`                                         | `COMPLEX*8`              | `ComplexF32`         | `Complex{Float32}`                                                                                          |
| `complex double`                                        | `COMPLEX*16`             | `ComplexF64`         | `Complex{Float64}`                                                                                          |
| `ptrdiff_t`                                             |                          | `Cptrdiff_t`         | `Int`                                                                                                       |
| `ssize_t`                                               |                          | `Cssize_t`           | `Int`                                                                                                       |
| `size_t`                                                |                          | `Csize_t`            | `UInt`                                                                                                      |
| `void`                                                  |                          |                      | `Cvoid`                                                                                                     |
| `void` and `[[noreturn]]` or `_Noreturn`                |                          |                      | `Union{}`                                                                                                   |
| `void*`                                                 |                          |                      | `Ptr{Cvoid}` (or similarly `Ref{Cvoid}`)                                                                    |
| `T*` (where T represents an appropriately defined type) |                          |                      | `Ref{T}` (T may be safely mutated only if T is an isbits type)                                              |
| `char*` (or `char[]`, e.g. a string)                    | `CHARACTER*N`            |                      | `Cstring` if null-terminated, or `Ptr{UInt8}` if not                                                        |
| `char**` (or `*char[]`)                                 |                          |                      | `Ptr{Ptr{UInt8}}`                                                                                           |
| `jl_value_t*` (any Julia Type)                          |                          |                      | `Any`                                                                                                       |
| `jl_value_t* const*` (a reference to a Julia value)     |                          |                      | `Ref{Any}` (const, since mutation would require a write barrier, which is not possible to insert correctly) |
| `va_arg`                                                |                          |                      | Not supported                                                                                               |
| `...` (variadic function specification)                 |                          |                      | `T...` (where `T` is one of the above types, when using the `ccall` function)                               |
| `...` (variadic function specification)                 |                          |                      | `; va_arg1::T, va_arg2::S, etc.` (only supported with `@ccall` macro)                                       |

[`Cstring`](@ref) türü, `Ptr{UInt8}` için esasen bir eşanlamlıdır; ancak `Cstring`'e dönüşüm, Julia dizesi herhangi bir gömülü null karakter içeriyorsa bir hata fırlatır (bu, C rutinini null'ı sonlandırıcı olarak kabul ederse dizeyi sessizce keser). Eğer bir C rutinine null sonlandırması varsaymayan bir `char*` geçiriyorsanız (örneğin, açık bir dize uzunluğu geçirdiğiniz için) veya Julia dizenizin kesinlikle null içermediğini biliyorsanız ve kontrolü atlamak istiyorsanız, argüman türü olarak `Ptr{UInt8}` kullanabilirsiniz. `Cstring` ayrıca [`ccall`](@ref) dönüş türü olarak da kullanılabilir, ancak bu durumda açıkça ek kontroller getirmez ve yalnızca çağrının okunabilirliğini artırmak için tasarlanmıştır.

**Sistem Bağımlı Türler**

| C name          | Standard Julia Alias | Julia Base Type                              |
|:--------------- |:-------------------- |:-------------------------------------------- |
| `char`          | `Cchar`              | `Int8` (x86, x86_64), `UInt8` (powerpc, arm) |
| `long`          | `Clong`              | `Int` (UNIX), `Int32` (Windows)              |
| `unsigned long` | `Culong`             | `UInt` (UNIX), `UInt32` (Windows)            |
| `wchar_t`       | `Cwchar_t`           | `Int32` (UNIX), `UInt16` (Windows)           |

!!! note
    Fortran'ı çağırırken, tüm girdiler yığın veya yığın tahsisli değerlere işaretçi olarak geçilmelidir, bu nedenle yukarıdaki tüm tür eşleşmeleri, tür spesifikasyonlarının etrafında ek bir `Ptr{..}` veya `Ref{..}` sarmalayıcı içermelidir.


!!! warning
    Dize argümanlar (`char*`) için Julia tipi `Cstring` olmalıdır (eğer null-terminasyonlu veri bekleniyorsa), aksi takdirde `Ptr{Cchar}` veya `Ptr{UInt8}` olmalıdır (bu iki işaretçi türü aynı etkiye sahiptir), yukarıda açıklandığı gibi, `String` değil. Benzer şekilde, dizi argümanları (`T[]` veya `T*`) için Julia tipi yine `Ptr{T}` olmalıdır, `Vector{T}` değil.


!!! warning
    Julia'nın `Char` tipi 32 bit'tir, bu da tüm platformlarda geniş karakter tipi (`wchar_t` veya `wint_t`) ile aynı değildir.


!!! warning
    `Union{}` dönüş tipi, fonksiyonun geri dönmeyeceği anlamına gelir, yani C++11 `[[noreturn]]` veya C11 `_Noreturn` (örneğin `jl_throw` veya `longjmp`). Değer döndürmeyen (`void`) ancak geri dönen fonksiyonlar için bunu kullanmayın, bunlar için `Cvoid` kullanın.


!!! note
    `wchar_t*` argümanları için, Julia tipi [`Cwstring`](@ref) olmalıdır (eğer C rutini null-terminatlı bir dize bekliyorsa), aksi takdirde `Ptr{Cwchar_t}` olmalıdır. Ayrıca, Julia'daki UTF-8 dize verileri dahili olarak null-terminatlıdır, bu nedenle kopya oluşturmadan null-terminatlı veri bekleyen C fonksiyonlarına geçirilebilir (ancak `Cwstring` tipi kullanmak, dize kendisi null karakterler içeriyorsa bir hata fırlatmasına neden olacaktır).


!!! note
    C fonksiyonları, `char**` türünde bir argüman aldıklarında, Julia içinde `Ptr{Ptr{UInt8}}` türü kullanılarak çağrılabilir. Örneğin, aşağıdaki gibi C fonksiyonları:

    ```c
    int main(int argc, char **argv);
    ```

    şu Julia kodu ile çağrılabilir:

    ```julia
    argv = [ "a.out", "arg1", "arg2" ]
    @ccall main(length(argv)::Int32, argv::Ptr{Ptr{UInt8}})::Int32
    ```


!!! note
    Fortran fonksiyonları `character(len=*)` türünde değişken uzunlukta dizgeler aldığında, dizge uzunlukları *gizli argümanlar* olarak sağlanır. Bu argümanların türü ve listede konumu derleyiciye özgüdür; derleyici satıcıları genellikle `Csize_t` türünü kullanmayı varsayılan olarak kabul eder ve gizli argümanları argüman listesinin sonuna ekler. Bu davranış bazı derleyiciler (GNU) için sabitken, diğerleri *isteğe bağlı olarak* gizli argümanları karakter argümanının hemen arkasına yerleştirmeye izin verir (Intel, PGI). Örneğin, aşağıdaki gibi Fortran alt yordamları

    ```fortran
    subroutine test(str1, str2)
    character(len=*) :: str1,str2
    ```

    şu Julia kodu ile çağrılabilir, burada uzunluklar eklenir

    ```julia
    str1 = "foo"
    str2 = "bar"
    ccall(:test, Cvoid, (Ptr{UInt8}, Ptr{UInt8}, Csize_t, Csize_t),
                        str1, str2, sizeof(str1), sizeof(str2))
    ```


!!! warning
    Fortran derleyicileri *gizli* argümanlar ekleyebilir, bu argümanlar işaretçiler, varsayılan şekilli (`:`) ve varsayılan boyutlu (`*`) diziler için geçerlidir. Bu tür bir davranış, `ISO_C_BINDING` kullanılarak ve alt programın tanımında `bind(c)` eklenerek önlenebilir; bu, uyumlu kod için şiddetle önerilir. Bu durumda, bazı dil özelliklerinin (örneğin, yalnızca `character(len=1)` dizeleri geçmek için izin verilecektir) bedeli karşılığında gizli argümanlar olmayacaktır.


!!! note
    Bir `Cvoid` döndüren bir C fonksiyonu, Julia'da `nothing` değerini döndürecektir.


### Struct Type Correspondences

Bileşen türleri, C'deki `struct` veya Fortran90'daki `TYPE` (veya bazı F77 varyantlarındaki `STRUCTURE` / `RECORD`) gibi, aynı alan düzenine sahip bir `struct` tanımı oluşturarak Julia'da yansıtılabilir.

`isbits` türleri özyinelemeli olarak kullanıldığında, satır içi olarak saklanır. Diğer tüm türler, verilere bir işaretçi olarak saklanır. C'de bir yapıyı başka bir yapının içinde değer olarak kullanırken, alanları manuel olarak kopyalamaya çalışmamanız çok önemlidir, çünkü bu doğru alan hizalamasını korumaz. Bunun yerine, bir `isbits` yapı türü tanımlayın ve onu kullanın. İsimlendirilmemiş yapılar, Julia'ya çeviride mümkün değildir.

Julia, packed struct ve union bildirimlerini desteklememektedir.

Bir `union`'ın yaklaşık bir değerini elde edebilirsiniz eğer, önceden, en büyük boyuta sahip olacak alanı (potansiyel olarak doldurma dahil) biliyorsanız. Alanlarınızı Julia'ya çevirirken, Julia alanını yalnızca o türde olacak şekilde tanımlayın.

Parametre dizileri `NTuple` ile ifade edilebilir. Örneğin, C notasyonundaki yapı şu şekilde yazılır:

```c
struct B {
    int A[3];
};

b_a_2 = B.A[2];
```

Julia olarak yazılabilir:

```julia
struct B
    A::NTuple{3, Cint}
end

b_a_2 = B.A[3]  # note the difference in indexing (1-based in Julia, 0-based in C)
```

Bilinmeyen boyutlu diziler (`[]` veya `[0]` ile belirtilen C99 uyumlu değişken uzunlukta yapılar) doğrudan desteklenmez. Genellikle bunlarla başa çıkmanın en iyi yolu, doğrudan bayt ofsetleriyle çalışmaktır. Örneğin, bir C kütüphanesi uygun bir dize türü tanımlayıp ona bir işaretçi döndürdüğünde:

```c
struct String {
    int strlen;
    char data[];
};
```

Julia'da, o dizeyi kopyalamak için parçalarına bağımsız olarak erişebiliriz:

```julia
str = from_c::Ptr{Cvoid}
len = unsafe_load(Ptr{Cint}(str))
unsafe_string(str + Core.sizeof(Cint), len)
```

### Type Parameters

`@ccall` ve `@cfunction` için tür argümanları, kullanımı içeren metod tanımlandığında statik olarak değerlendirilir. Bu nedenle, bir değişken değil, bir literal demet biçiminde olmalı ve yerel değişkenlere referans veremez.

Bu garip bir kısıtlama gibi gelebilir, ancak C'nin Julia gibi dinamik bir dil olmadığını unutmayın; bu nedenle, fonksiyonları yalnızca statik olarak bilinen, sabit bir imzaya sahip argüman türlerini kabul edebilir.

Ancak, tür düzeninin, amaçlanan C ABI'yi hesaplamak için statik olarak bilinmesi gerekirken, fonksiyonun statik parametreleri bu statik ortamın bir parçası olarak kabul edilir. Fonksiyonun statik parametreleri, tür düzenini etkilemedikleri sürece, çağrı imzasında tür parametreleri olarak kullanılabilir. Örneğin, `f(x::T) where {T} = @ccall valid(x::Ptr{T})::Ptr{T}` geçerlidir, çünkü `Ptr` her zaman bir kelime boyutunda ilkel bir türdür. Ancak, `g(x::T) where {T} = @ccall notvalid(x::T)::T` geçerli değildir, çünkü `T`'nin tür düzeni statik olarak bilinmemektedir.

### SIMD Values

Not: Bu özellik şu anda yalnızca 64-bit x86 ve AArch64 platformlarında uygulanmıştır.

Eğer bir C/C++ rutini, bir argümanı veya dönüş değerini yerel bir SIMD türü olarak alıyorsa, karşılık gelen Julia türü, SIMD türüne doğal olarak eşleşen `VecElement`'in homojen bir demetidir. Özellikle:

>   * Tuple, SIMD türüyle aynı boyutta olmalıdır. Örneğin, x86'da bir `__m128`'i temsil eden bir tuple'ın boyutu 16 bayt olmalıdır.
>   * Tuple'un eleman türü, `T`'nin 1, 2, 4 veya 8 byte'lık bir ilkel tür olduğu `VecElement{T}` örneği olmalıdır.


Örneğin, AVX intrinsics kullanan bu C rutinini düşünün:

```c
#include <immintrin.h>

__m256 dist( __m256 a, __m256 b ) {
    return _mm256_sqrt_ps(_mm256_add_ps(_mm256_mul_ps(a, a),
                                        _mm256_mul_ps(b, b)));
}
```

Aşağıdaki Julia kodu `ccall` kullanarak `dist` fonksiyonunu çağırır:

```julia
const m256 = NTuple{8, VecElement{Float32}}

a = m256(ntuple(i -> VecElement(sin(Float32(i))), 8))
b = m256(ntuple(i -> VecElement(cos(Float32(i))), 8))

function call_dist(a::m256, b::m256)
    @ccall "libdist".dist(a::m256, b::m256)::m256
end

println(call_dist(a,b))
```

Ana makine gerekli SIMD kayıtlarına sahip olmalıdır. Örneğin, yukarıdaki kod AVX desteği olmayan ana makinelerde çalışmayacaktır.

### Memory Ownership

**`malloc`/`free`**

Bellek tahsisi ve bu tür nesnelerin serbest bırakılması, kullanılan kütüphanelerdeki uygun temizleme rutinlerine yapılan çağrılarla yönetilmelidir, tıpkı herhangi bir C programında olduğu gibi. Julia'da [`Libc.free`](@ref) ile bir C kütüphanesinden alınan bir nesneyi serbest bırakmaya çalışmayın, çünkü bu, `free` fonksiyonunun yanlış kütüphane aracılığıyla çağrılmasına ve sürecin sona ermesine neden olabilir. Tersine (Julia'da tahsis edilen bir nesnenin bir dış kütüphane tarafından serbest bırakılması) de geçersizdir.

### When to use `T`, `Ptr{T}` and `Ref{T}`

In Julia code wrapping calls to external C routines, ordinary (non-pointer) data should be declared to be of type `T` inside the `@ccall`, as they are passed by value. For C code accepting pointers, [`Ref{T}`](@ref) should generally be used for the types of input arguments, allowing the use of pointers to memory managed by either Julia or C through the implicit call to [`Base.cconvert`](@ref). In contrast, pointers returned by the C function called should be declared to be of the output type [`Ptr{T}`](@ref), reflecting that the memory pointed to is managed by C only. Pointers contained in C structs should be represented as fields of type `Ptr{T}` within the corresponding Julia struct types designed to mimic the internal structure of corresponding C structs.

Julia kodunda dış Fortran rutinlerine yapılan çağrıları sarmalarken, tüm girdi argümanları `Ref{T}` türünde tanımlanmalıdır, çünkü Fortran tüm değişkenleri bellek konumlarına işaretçi olarak geçirir. Dönüş türü, Fortran alt programları için ya `Cvoid` olmalı ya da `T` türünü döndüren Fortran fonksiyonları için bir `T` olmalıdır.

## Mapping C Functions to Julia

### `@ccall` / `@cfunction` argument translation guide

C argüman listesini Julia'ya çevirmek için:

  * `T`, burada `T` aşağıdaki ilkel türlerden biridir: `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` veya bunların herhangi bir `typedef` eşdeğeri

      * `T`, burada `T` yukarıdaki tabloda belirtilen eşdeğer Julia Bits Tipidir.
      * eğer `T` bir `enum` ise, argüman türü `Cint` veya `Cuint` ile eşdeğer olmalıdır.
      * argüman değeri kopyalanacak (değer ile geçilecek)
  * `struct T` (bir yapıya typedef dahil)

      * `T`, burada `T` bir Julia yaprak türüdür.
      * argüman değeri kopyalanacak (değer ile geçilecek)
  * `void*`

      * parametre nasıl kullanıldığına bağlıdır, önce bunu hedef işaretçi türüne çevirin, ardından bu listedeki kalan kuralları kullanarak Julia eşdeğerini belirleyin
      * bu argüman gerçekten sadece bilinmeyen bir işaretçi ise `Ptr{Cvoid}` olarak tanımlanabilir.
  * `jl_value_t*`

      * `Herhangi bir`
      * argüman değeri geçerli bir Julia nesnesi olmalıdır
  * `jl_value_t* const*`

      * `Ref{Herhangi}`
      * argüman listesi geçerli bir Julia nesnesi (veya `C_NULL`) olmalıdır
      * bir çıktı parametresi için kullanılamaz, kullanıcı nesnenin GC tarafından korunmasını ayrı olarak düzenleyemezse
  * `T*`

      * `Ref{T}`, burada `T`, `T` ile ilgili Julia türüdür.
      * argüman değeri, `inlinealloc` türü ise (bu `isbits`'i içerir) kopyalanacaktır, aksi takdirde değer geçerli bir Julia nesnesi olmalıdır.
  * `T (*)(...)` (örneğin, bir işlevin işaretçisi)

      * `Ptr{Cvoid}` (bu işaretçiyi oluşturmak için [`@cfunction`](@ref) ifadesini açıkça kullanmanız gerekebilir)
  * `...` (örneğin bir vararg)

      * [`ccall` için]: `T...`, burada `T`, kalan tüm argümanların tek Julia türüdür.
      * [for `@ccall`]: `; va_arg1::T, va_arg2::S, vb.` gibi, burada `T` ve `S` Julia türüdür (yani, normal argümanları varargs'tan `;` ile ayırın)
      * şu anda `@cfunction` tarafından desteklenmiyor
  * `va_arg`

      * `ccall` veya `@cfunction` tarafından desteklenmiyor

### `@ccall` / `@cfunction` return type translation guide

C'den Julia'ya bir dönüş türünü çevirmek için:

  * `boş`

      * `Cvoid` (bu, singleton örneği `nothing::Cvoid` döndürecektir)
  * `T`, burada `T` aşağıdaki ilkel türlerden biridir: `char`, `int`, `long`, `short`, `float`, `double`, `complex`, `enum` veya bunların herhangi bir `typedef` eşdeğeri

      * `T`, burada `T` yukarıdaki tabloda belirtilen eşdeğer Julia Bits Tipidir.
      * eğer `T` bir `enum` ise, argüman türü `Cint` veya `Cuint` ile eşdeğer olmalıdır.
      * argüman değeri kopyalanacak (değer ile döndürülecek)
  * `struct T` (bir yapıya typedef dahil)

      * `T`, burada `T` bir Julia Yaprak Türüdür.
      * argüman değeri kopyalanacak (değer ile döndürülecek)
  * `void*`

      * parametre nasıl kullanıldığına bağlıdır, önce bunu hedef işaretçi türüne çevirin, ardından bu listedeki kalan kuralları kullanarak Julia eşdeğerini belirleyin
      * bu argüman gerçekten sadece bilinmeyen bir işaretçi ise `Ptr{Cvoid}` olarak tanımlanabilir
  * `jl_value_t*`

      * `Herhangi bir`
      * argüman değeri geçerli bir Julia nesnesi olmalıdır
  * `jl_value_t**`

      * `Ptr{Any}` (`Ref{Any}` geçerli bir dönüş tipi değildir)
  * `T*`

      * Eğer bellek zaten Julia tarafından sahiplenilmişse veya bir `isbits` türüyse ve null olmadığı biliniyorsa:

          * `Ref{T}`, burada `T`, `T` ile ilgili Julia türüdür.
          * `Ref{Any}` dönüş türü geçersizdir, ya `jl_value_t*` ile karşılık gelen `Any` olmalı ya da `jl_value_t**` ile karşılık gelen `Ptr{Any}` olmalıdır.
          * C **MUST NOT** `Ref{T}` ile döndürülen belleği değiştirmek `T` bir `isbits` türü ise
      * Eğer bellek C tarafından sahipse:

          * `Ptr{T}`, burada `T`, `T`'ye karşılık gelen Julia türüdür.
  * `T (*)(...)` (örneğin, bir işlevin işaretçisi)

      * `Ptr{Cvoid}` doğrudan Julia'dan çağırmak için bunu `@ccall`'e ilk argüman olarak geçirmeniz gerekecek. [Indirect Calls](@ref)'ya bakın.

### Passing Pointers for Modifying Inputs

Çünkü C birden fazla dönüş değerini desteklemediğinden, genellikle C fonksiyonları, fonksiyonun değiştireceği verilere işaretçi alır. Bunu bir `@ccall` içinde başarmak için, önce değeri uygun türde bir [`Ref{T}`](@ref) içine kapsüllemeniz gerekir. Bu `Ref` nesnesini bir argüman olarak geçtiğinizde, Julia otomatik olarak kapsüllenmiş verilere bir C işaretçisi geçecektir:

```julia
width = Ref{Cint}(0)
range = Ref{Cfloat}(0)
@ccall foo(width::Ref{Cint}, range::Ref{Cfloat})::Cvoid
```

Dönüşte, `width` ve `range`'in içeriği (eğer `foo` tarafından değiştirildiyse) `width[]` ve `range[]` ile alınabilir; yani, sıfır boyutlu diziler gibi davranırlar.

## C Wrapper Examples

Basit bir `Ptr` türü döndüren bir C sarmalayıcı örneğiyle başlayalım:

```julia
mutable struct gsl_permutation
end

# The corresponding C signature is
#     gsl_permutation * gsl_permutation_alloc (size_t n);
function permutation_alloc(n::Integer)
    output_ptr = @ccall "libgsl".gsl_permutation_alloc(n::Csize_t)::Ptr{gsl_permutation}
    if output_ptr == C_NULL # Could not allocate memory
        throw(OutOfMemoryError())
    end
    return output_ptr
end
```

[GNU Scientific Library](https://www.gnu.org/software/gsl/) (burada `:libgsl` üzerinden erişilebilir olduğu varsayılmaktadır) C fonksiyonu `gsl_permutation_alloc`'un dönüş tipi olarak opak bir işaretçi, `gsl_permutation *`, tanımlar. Kullanıcı kodu asla `gsl_permutation` yapısının içine bakmak zorunda olmadığından, ilgili Julia sarmalayıcısının yalnızca iç alanları olmayan ve tek amacı bir `Ptr` türünün tür parametresine yerleştirilmek olan yeni bir tür bildirimi, `gsl_permutation`, gereklidir. [`ccall`](@ref)'nın dönüş tipi `Ptr{gsl_permutation}` olarak bildirilmiştir, çünkü `output_ptr` tarafından kontrol edilen ve işaret edilen bellek C tarafından yönetilmektedir.

Girdi `n` değer olarak geçilir, bu nedenle fonksiyonun girdi imzası basitçe `::Csize_t` olarak tanımlanmıştır, herhangi bir `Ref` veya `Ptr` gerekli değildir. (Eğer sarmalayıcı bir Fortran fonksiyonunu çağırıyorsa, ilgili fonksiyon girdi imzası bunun yerine `::Ref{Csize_t}` olur, çünkü Fortran değişkenleri işaretçilerle geçilir.) Ayrıca, `n` herhangi bir `Csize_t` tamsayıya dönüştürülebilen bir tür olabilir; [`ccall`](@ref) dolaylı olarak [`Base.cconvert(Csize_t, n)`](@ref) çağrısını yapar.

İşte ilgili yıkıcının sarıldığı ikinci bir örnek:

```julia
# The corresponding C signature is
#     void gsl_permutation_free (gsl_permutation * p);
function permutation_free(p::Ptr{gsl_permutation})
    @ccall "libgsl".gsl_permutation_free(p::Ptr{gsl_permutation})::Cvoid
end
```

İşte Julia dizilerini geçiren üçüncü bir örnek:

```julia
# The corresponding C signature is
#    int gsl_sf_bessel_Jn_array (int nmin, int nmax, double x,
#                                double result_array[])
function sf_bessel_Jn_array(nmin::Integer, nmax::Integer, x::Real)
    if nmax < nmin
        throw(DomainError())
    end
    result_array = Vector{Cdouble}(undef, nmax - nmin + 1)
    errorcode = @ccall "libgsl".gsl_sf_bessel_Jn_array(
                    nmin::Cint, nmax::Cint, x::Cdouble, result_array::Ref{Cdouble})::Cint
    if errorcode != 0
        error("GSL error code $errorcode")
    end
    return result_array
end
```

C fonksiyonu wrapped, bir tamsayı hata kodu döndürür; Bessel J fonksiyonunun gerçek değerlendirmesinin sonuçları Julia dizisi `result_array`'yi doldurur. Bu değişken, belleği Julia tarafından tahsis edilen ve yönetilen bir `Ref{Cdouble}` olarak tanımlanmıştır. [`Base.cconvert(Ref{Cdouble}, result_array)`](@ref) ifadesine yapılan örtük çağrı, Julia işaretçisini C tarafından anlaşılabilir bir forma dönüştürerek bir Julia dizi veri yapısına açar.

## Fortran Wrapper Example

Aşağıdaki örnek, bir nokta çarpımını hesaplamak için yaygın bir Fortran kütüphanesi (libBLAS) içindeki bir işlevi çağırmak üzere `ccall` kullanır. Burada, argüman eşlemesinin yukarıdakinden biraz farklı olduğunu unutmayın; çünkü Julia'dan Fortran'a eşleme yapmamız gerekiyor. Her argüman türü için `Ref` veya `Ptr` belirtiriz. Bu adlandırma kuralı, Fortran derleyiciniz ve işletim sisteminiz için özel olabilir ve muhtemelen belgelenmemiştir. Ancak, her birini `Ref` (veya eşdeğer olduğunda `Ptr`) içine sarmak, Fortran derleyici uygulamalarının sık karşılaşılan bir gereksinimidir:

```julia
function compute_dot(DX::Vector{Float64}, DY::Vector{Float64})
    @assert length(DX) == length(DY)
    n = length(DX)
    incx = incy = 1
    product = @ccall "libLAPACK".ddot(
        n::Ref{Int32}, DX::Ptr{Float64}, incx::Ref{Int32}, DY::Ptr{Float64}, incy::Ref{Int32})::Float64
    return product
end
```

## Garbage Collection Safety

Veri geçerken bir `@ccall`'e, [`pointer`](@ref) fonksiyonunu kullanmaktan kaçınmak en iyisidir. Bunun yerine, [`Base.cconvert`](@ref) metodunu tanımlayın ve değişkenleri doğrudan `@ccall`'e geçirin. `@ccall`, tüm argümanlarının çağrı geri dönene kadar çöp toplama işlemlerinden korunmasını otomatik olarak düzenler. Eğer bir C API'si, Julia tarafından tahsis edilen bir bellek referansını saklayacaksa, `@ccall` geri döndükten sonra, nesnenin çöp toplayıcıya görünür kalmasını sağlamalısınız. Bunu yapmanın önerilen yolu, C kütüphanesi sizinle işini bitirdiğini bildirmeden önce bu değerleri tutmak için `Array{Ref,1}` türünde bir global değişken oluşturmaktır.

Herhangi bir Julia verisine işaretçi oluşturduğunuzda, işaretçiyi kullanmayı bitirdiğiniz zamana kadar orijinal verinin var olduğundan emin olmalısınız. Julia'daki [`unsafe_load`](@ref) ve [`String`](@ref) gibi birçok yöntem, verinin sahipliğini almak yerine kopyalarını oluşturur, böylece orijinal veriyi serbest bırakmak (veya değiştirmek) Julia'yı etkilemeden güvenli bir şekilde yapılabilir. Dikkate değer bir istisna, performans nedenleriyle, temel tamponun sahipliğini paylaşan (veya sahipliğini alması için talimat verilebilen) [`unsafe_wrap`](@ref)'dır.

Çöp toplayıcı, herhangi bir sonlandırma sırasını garanti etmez. Yani, eğer `a`, `b`'ye bir referans içeriyorsa ve hem `a` hem de `b` çöp toplama için uygun ise, `b`'nin `a`'dan sonra sonlandırılacağına dair bir garanti yoktur. Eğer `a`'nın düzgün bir şekilde sonlandırılması `b`'nin geçerli olmasına bağlıysa, bu başka yollarla ele alınmalıdır.

## Non-constant Function Specifications

Bazen, gerekli kütüphanenin tam adı veya yolu önceden bilinmemekte ve çalışma zamanında hesaplanması gerekmektedir. Bu tür durumları ele almak için, kütüphane bileşeni spesifikasyonu bir fonksiyon çağrısı olabilir, örneğin `find_blas().dgemm`. Çağrı ifadesi, `ccall` kendisi yürütüldüğünde gerçekleştirilecektir. Ancak, kütüphane konumunun belirlendikten sonra değişmeyeceği varsayılmaktadır, bu nedenle çağrının sonucu önbelleğe alınabilir ve yeniden kullanılabilir. Bu nedenle, ifadenin kaç kez yürütüleceği belirsizdir ve birden fazla çağrı için farklı değerler döndürmek belirsiz bir davranışa yol açar.

Eğer daha fazla esneklik gerekiyorsa, [`eval`](@ref) üzerinden aşamalı olarak işlev adları olarak hesaplanan değerler kullanmak mümkündür:

```julia
@eval @ccall "lib".$(string("a", "b"))()::Cint
```

Bu ifade, `string` kullanarak bir isim oluşturur, ardından bu ismi yeni bir `@ccall` ifadesine yerleştirir ve bu ifade değerlendirilir. `eval`'in yalnızca en üst düzeyde çalıştığını unutmayın, bu nedenle bu ifade içinde yerel değişkenler mevcut olmayacaktır (değerleri `$` ile yer değiştirilmedikçe). Bu nedenle, `eval` genellikle yalnızca üst düzey tanımlar oluşturmak için kullanılır; örneğin, birçok benzer işlev içeren kütüphaneleri sarmak için. [`@cfunction`](@ref) için benzer bir örnek oluşturulabilir.

Ancak, bunu yapmak aynı zamanda çok yavaş olacak ve bellek sızıntısına neden olacaktır, bu yüzden genellikle bunu kaçınmalısınız ve bunun yerine okumaya devam etmelisiniz. Bir sonraki bölüm, dolaylı çağrıları kullanarak benzer bir etkiyi verimli bir şekilde nasıl elde edeceğinizi tartışmaktadır.

## Indirect Calls

`@ccall`'in ilk argümanı, çalışma zamanında değerlendirilen bir ifade de olabilir. Bu durumda, ifade bir `Ptr` olarak değerlendirilmelidir; bu, çağrılacak yerel işlevin adresi olarak kullanılacaktır. Bu davranış, ilk `@ccall` argümanının yerel değişkenler, işlev argümanları veya sabit olmayan global değişkenler gibi sabit olmayan referanslar içerdiği durumlarda gerçekleşir.

Örneğin, işlevi `dlsym` aracılığıyla arayabilir ve ardından o oturum için paylaşılan bir referansta önbelleğe alabilirsiniz. Örneğin:

```julia
macro dlsym(lib, func)
    z = Ref{Ptr{Cvoid}}(C_NULL)
    quote
        let zlocal = $z[]
            if zlocal == C_NULL
                zlocal = dlsym($(esc(lib))::Ptr{Cvoid}, $(esc(func)))::Ptr{Cvoid}
                $z[] = zlocal
            end
            zlocal
        end
    end
end

mylibvar = Libdl.dlopen("mylib")
@ccall $(@dlsym(mylibvar, "myfunc"))()::Cvoid
```

## Closure cfunctions

[`@cfunction`](@ref)'ya ilk argüman bir `$` ile işaretlenebilir, bu durumda dönen değer bir `struct CFunction` olacaktır ve bu argümanı kapsayacaktır. Bu dönen nesnenin, tüm kullanımları tamamlanana kadar canlı tutulmasını sağlamalısınız. C işlevselliği genellikle gerekli değildir, çünkü bu işlevsellik C'de mevcut değildir, ancak ayrı bir kapanış ortamı parametresi sağlamayan kötü tasarlanmış API'lerle başa çıkmak için yararlı olabilir. [`finalizer`](@ref) ile bu referans bırakıldığında ve atexit ile bu içerik ve kod cfunction işaretçisi üzerinden silinecektir.

```julia
function qsort(a::Vector{T}, cmp) where T
    isbits(T) || throw(ArgumentError("this method can only qsort isbits arrays"))
    callback = @cfunction $cmp Cint (Ref{T}, Ref{T})
    # Here, `callback` isa Base.CFunction, which will be converted to Ptr{Cvoid}
    # (and protected against finalization) by the ccall
    @ccall qsort(a::Ptr{T}, length(a)::Csize_t, Base.elsize(a)::Csize_t, callback::Ptr{Cvoid})
    # We could instead use:
    #    GC.@preserve callback begin
    #        use(Base.unsafe_convert(Ptr{Cvoid}, callback))
    #    end
    # if we needed to use it outside of a `ccall`
    return a
end
```

!!! note
    Kapatma [`@cfunction`](@ref), tüm platformlarda mevcut olmayan LLVM trampolinlerine dayanır (örneğin ARM ve PowerPC).


## Closing a Library

Bazen bir kütüphaneyi kapatmak (boşaltmak) yeniden yüklenebilmesi için faydalı olabilir. Örneğin, Julia ile kullanılmak üzere C kodu geliştirirken, C kodunu derleyip, Julia'dan çağırmak, ardından kütüphaneyi kapatmak, bir düzenleme yapmak, yeniden derlemek ve yeni değişiklikleri yüklemek gerekebilir. Julia'yı yeniden başlatabilir veya kütüphaneyi açıkça yönetmek için `Libdl` fonksiyonlarını kullanabilirsiniz, örneğin:

```julia
lib = Libdl.dlopen("./my_lib.so") # Open the library explicitly.
sym = Libdl.dlsym(lib, :my_fcn)   # Get a symbol for the function to call.
@ccall $sym(...) # Use the pointer `sym` instead of the library.symbol tuple.
Libdl.dlclose(lib) # Close the library explicitly.
```

Not edin ki `@ccall` kullanırken girdi (örneğin, `@ccall "./my_lib.so".my_fcn(...)::Cvoid`) ile, kütüphane örtük olarak açılır ve açıkça kapatılmayabilir.

## Variadic function calls

Variadic C fonksiyonlarını çağırmak için, gerekli argümanları variadic argümanlardan ayırmak için argüman listesinde bir `noktalı virgül` kullanılabilir. Aşağıda `printf` fonksiyonu ile bir örnek verilmiştir:

```julia-repl
julia> @ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
foo = 3
8
```

## [`ccall` interface](@id ccall-interface)

Başka bir alternatif arayüzü `@ccall` vardır. Bu arayüz biraz daha az kullanışlıdır ancak bir [calling convention](@ref calling-convention) belirtmeye olanak tanır.

[`ccall`](@ref) argümanları şunlardır:

1. A `(:function, "kütüphane")` çifti (en yaygın),

    VEYA

    bir `:function` adı sembolü veya `"function"` adı dizesi (mevcut işlem veya libc'deki semboller için),

    VEYA

    bir işlev işaretçisi (örneğin, `dlsym`'den).
2. Fonksiyonun dönüş tipi
3. Bir işlev imzasına karşılık gelen bir girdi türleri demeti. Yaygın bir hata, bir argüman türleri 1-demeti yazarken sonuna bir virgül eklemeyi unutmaktır.
4. Fonksiyona geçilecek gerçek argüman değerleri, varsa; her biri ayrı bir parametredir.

!!! note
    `(:function, "library")` çifti, dönüş türü ve girdi türleri, literal sabitler olmalıdır (yani, değişken olamazlar, ancak [Non-constant Function Specifications](@ref)'ya bakın).

    Kalan parametreler, içeren metod tanımlandığında derleme zamanında değerlendirilir.


Aşağıda makro ve fonksiyon arayüzleri arasındaki çevirilerin bir tablosu verilmiştir.

|                                                                     `@ccall` |                                                                     `ccall` |
| ----------------------------------------------------------------------------:| ---------------------------------------------------------------------------:|
|                                                      `@ccall clock()::Int32` |                                                  `ccall(:clock, Int32, ())` |
|                                                    `@ccall f(a::Cint)::Cint` |                                               `ccall(:a, Cint, (Cint,), a)` |
|                               `@ccall "mylib".f(a::Cint, b::Cdouble)::Cvoid` |                      `ccall((:f, "mylib"), Cvoid, (Cint, Cdouble), (a, b))` |
|                                                    `@ccall $fptr.f()::Cvoid` |                                                 `ccall(fptr, f, Cvoid, ())` |
|      `@ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint` |                                                             `<unavailable>` |
| `@ccall printf("%s = %s\n"::Cstring ; "2 + 2"::Cstring, "5"::Cstring)::Cint` |    `ccall(:printf, Cint, (Cstring, Cstring...), "%s = %s\n", "2 + 2", "5")` |
|                                                              `<unavailable>` | `ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))` |

## [Calling Convention](@id calling-convention)

`ccall`'in ikinci argümanı (dönüş türünden hemen önce) isteğe bağlı olarak bir çağrı sözleşmesi belirleyicisi olabilir (şu anda `@ccall` makrosu bir çağrı sözleşmesi vermeyi desteklemiyor). Herhangi bir belirleyici olmadan, platforma özgü varsayılan C çağrı sözleşmesi kullanılır. Diğer desteklenen sözleşmeler: `stdcall`, `cdecl`, `fastcall` ve `thiscall` (64-bit Windows'ta no-op). Örneğin ( `base/libc.jl`'den) yukarıdaki gibi aynı `gethostname``ccall`'i görüyoruz, ancak Windows için doğru imza ile:

```julia
hn = Vector{UInt8}(undef, 256)
err = ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))
```

Daha fazla bilgi için lütfen [LLVM Language Reference](https://llvm.org/docs/LangRef.html#calling-conventions) adresine bakın.

Bir ek özel çağrı sözleşmesi [`llvmcall`](@ref Base.llvmcall) bulunmaktadır; bu, LLVM intrinsics'lerine doğrudan çağrılar eklemeye olanak tanır. Bu, GPGPU'lar gibi alışılmadık platformlara hedeflenirken özellikle yararlı olabilir. Örneğin, [CUDA](https://llvm.org/docs/NVPTXUsage.html) için, iş parçacığı indeksini okuyabilmemiz gerekiyor:

```julia
ccall("llvm.nvvm.read.ptx.sreg.tid.x", llvmcall, Int32, ())
```

Herhangi bir `ccall` ile olduğu gibi, argüman imzasının tam olarak doğru olması esastır. Ayrıca, `Core.Intrinsics` tarafından sunulan eşdeğer Julia fonksiyonlarının aksine, içselin mantıklı olmasını ve mevcut hedef üzerinde çalışmasını sağlayan bir uyumluluk katmanı olmadığını unutmayın.

## Accessing Global Variables

Yerel kütüphaneler tarafından dışa aktarılan global değişkenler, [`cglobal`](@ref) fonksiyonu kullanılarak isimleriyle erişilebilir. `4d61726b646f776e2e436f64652822222c202263676c6f62616c2229_40726566` fonksiyonuna verilen argümanlar, [`ccall`](@ref) tarafından kullanılan sembol spesifikasyonuna benzer bir biçimde ve değişkenin içinde saklanan değeri tanımlayan bir tür içerir:

```julia-repl
julia> cglobal((:errno, :libc), Int32)
Ptr{Int32} @0x00007f418d0816b8
```

Sonuç, değerin adresini veren bir işaretçidir. Bu değer, bu işaretçi aracılığıyla [`unsafe_load`](@ref) ve [`unsafe_store!`](@ref) kullanılarak manipüle edilebilir.

!!! note
    Bu `errno` sembolü "libc" adlı bir kütüphanede bulunmayabilir, çünkü bu, sistem derleyicinizin bir uygulama ayrıntısıdır. Genellikle standart kütüphane sembollerine yalnızca isimle erişilmelidir, bu da derleyicinin doğru olanı doldurmasına olanak tanır. Ancak, bu örnekte gösterilen `errno` sembolü çoğu derleyicide özeldir, bu nedenle burada görülen değer muhtemelen beklediğiniz veya istediğiniz şey değildir. C dilinde eşzamanlı çoklu iş parçacığına sahip herhangi bir sistemde eşdeğer kodu derlemek, genellikle aslında farklı bir işlevi çağırır (makro ön işleyici aşırı yüklemesi aracılığıyla) ve burada yazdırılan eski değerden farklı bir sonuç verebilir.


## Accessing Data through a Pointer

Aşağıdaki yöntemler "güvensiz" olarak tanımlanmıştır çünkü kötü bir işaretçi veya tür beyanı, Julia'nın aniden sona ermesine neden olabilir.

Verilen bir `Ptr{T}` ile, `T` türündeki içerikler genellikle `unsafe_load(ptr, [index])` kullanılarak referans edilen bellekten bir Julia nesnesine kopyalanabilir. İndeks argümanı isteğe bağlıdır (varsayılan 1'dir) ve Julia'nın 1 tabanlı indeksleme kuralını takip eder. Bu fonksiyon, [`getindex`](@ref) ve [`setindex!`](@ref) (örneğin `[]` erişim sözdizimi) davranışına kasıtlı olarak benzer şekilde tasarlanmıştır.

Dönüş değeri, referans alınan belleğin içeriğinin bir kopyasını içerecek şekilde başlatılmış yeni bir nesne olacaktır. Referans alınan bellek güvenle serbest bırakılabilir veya salınabilir.

Eğer `T` `Herhangi` ise, o zaman belleğin bir Julia nesnesine (bir `jl_value_t*`) referans içerdiği varsayılır, sonuç bu nesneye bir referans olacaktır ve nesne kopyalanmayacaktır. Bu durumda, nesnenin her zaman çöp toplayıcıya görünür olduğundan emin olmak için dikkatli olmalısınız (işaretçiler sayılmaz, ancak yeni referans sayılır) böylece bellek gereksiz yere serbest bırakılmaz. Nesne başlangıçta Julia tarafından tahsis edilmemişse, yeni nesne asla Julia'nın çöp toplayıcısı tarafından sonlandırılmayacaktır. Eğer `Ptr` kendisi aslında bir `jl_value_t*` ise, [`unsafe_pointer_to_objref(ptr)`](@ref) ile tekrar bir Julia nesne referansına dönüştürülebilir. (Julia değerleri `v`, [`pointer_from_objref(v)`](@ref) çağrılarak `Ptr{Cvoid}` işaretçilerine dönüştürülebilir.)

Tersine işlem (`Ptr{T}`'ye veri yazma), [`unsafe_store!(ptr, value, [index])`](@ref) kullanılarak gerçekleştirilebilir. Şu anda, bu yalnızca ilkel türler veya diğer işaretçi içermeyen (`isbits`) değişmez yapı türleri için desteklenmektedir.

Herhangi bir hata fırlatan işlem muhtemelen şu anda uygulanmamıştır ve çözülmesi için bir hata olarak bildirilmelidir.

Eğer ilgi alanındaki işaretçi düz veri dizisi (ilkel tür veya değişmez yapı) ise, [`unsafe_wrap(Array, ptr,dims, own = false)`](@ref) fonksiyonu daha yararlı olabilir. Son parametre, Julia'nın temel tamponun "sahipliğini alması" ve döndürülen `Array` nesnesi sonlandırıldığında `free(ptr)` çağrısı yapması gerektiğinde true olmalıdır. Eğer `own` parametresi atlanırsa veya false ise, çağrıcı, tamponun tüm erişim tamamlanana kadar varlığını sürdürmesini sağlamalıdır.

`Ptr` türü üzerinde aritmetik işlemler (örneğin, `+` kullanarak) Julia'da C'nin işaretçi aritmetiği ile aynı şekilde davranmaz. Julia'da bir `Ptr`'ye bir tamsayı eklemek, her zaman işaretçiyi bazı *baytlar* kadar hareket ettirir, elemanlar değil. Bu şekilde, işaretçi aritmetiğinden elde edilen adres değerleri, işaretçilerin eleman türlerine bağlı değildir.

## Thread-safety

Bazı C kütüphaneleri geri çağırmalarını farklı bir iş parçacığından yürütür ve Julia iş parçacığı güvenli olmadığından bazı ek önlemler almanız gerekecek. Özellikle, iki katmanlı bir sistem kurmanız gerekecek: C geri çağrısı yalnızca "gerçek" geri çağrınızın yürütülmesini (Julia'nın olay döngüsü aracılığıyla) *planlamalıdır*. Bunu yapmak için bir [`AsyncCondition`](@ref Base.AsyncCondition) nesnesi oluşturun ve üzerinde [`wait`](@ref) çağrısında bulunun:

```julia
cond = Base.AsyncCondition()
wait(cond)
```

Geçtiğiniz geri çağırma, yalnızca [`ccall`](@ref)'yı `:uv_async_send`'e çalıştırmalı, `cond.handle`'ı argüman olarak geçmeli ve Julia çalışma zamanı ile herhangi bir tahsisat veya diğer etkileşimlerden kaçınmalıdır.

Olayların birleştirilebileceğini unutmayın, bu nedenle `uv_async_send`'e birden fazla çağrı, koşula tek bir uyanma bildirimi ile sonuçlanabilir.

## More About Callbacks

Daha fazla bilgi için C kütüphanelerine geri çağırmaların nasıl geçirileceği hakkında, bu [blog post](https://julialang.org/blog/2013/05/callback) adresine bakın.

## C++

C++ bağlamaları oluşturmak için araçlar için [CxxWrap](https://github.com/JuliaInterop/CxxWrap.jl) paketine bakın.

[^1]: Non-library function calls in both C and Julia can be inlined and thus may have even less overhead than calls to shared library functions. The point above is that the cost of actually doing foreign function call is about the same as doing a call in either native language.

[^2]: The [Clang package](https://github.com/ihnorton/Clang.jl) can be used to auto-generate Julia code from a C header file.
