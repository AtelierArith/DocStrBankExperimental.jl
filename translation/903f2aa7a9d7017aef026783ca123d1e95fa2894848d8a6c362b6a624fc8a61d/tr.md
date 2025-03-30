# [Scoped Values](@id scoped-values)

Scoped values provide an implementation of dynamic scoping in Julia.

!!! note "Lexical scoping vs dynamic scoping"
    [Lexical scoping](@ref scope-of-variables) Julia'da varsayılan davranıştır. Sözdizimsel kapsam altında bir değişkenin kapsamı, bir programın sözdizimsel (metinsel) yapısı tarafından belirlenir. Dinamik kapsam altında bir değişken, programın yürütülmesi sırasında en son atanan değere bağlıdır.


Kapsamlı bir değerin durumu, programın yürütme yoluna bağlıdır. Bu, kapsamlı bir değer için aynı anda birden fazla farklı değeri gözlemleyebileceğiniz anlamına gelir.

!!! compat "Julia 1.11"
    Scoped değerler Julia 1.11'de tanıtıldı. Julia 1.8+ sürümünde, ScopedValues.jl paketinden uyumlu bir uygulama mevcuttur.


En en basit formda, varsayılan bir değer ile [`ScopedValue`](@ref Base.ScopedValues.ScopedValue) oluşturabilirsiniz ve ardından [`with`](@ref Base.ScopedValues.with) veya [`@with`](@ref Base.ScopedValues.@with) kullanarak yeni bir dinamik kapsam girebilirsiniz. Yeni kapsam, sağlanan kapsamlı değerin önceki tanımlamalar üzerinde önceliğe sahip olduğu ile birlikte, üst kapsamdan (ve tüm dış kapsamdan) tüm değerleri miras alacaktır.

Öncelikle **leksikal** kapsamın bir örneğine bakalım. Bir `let` ifadesi, dıştaki `x` tanımının içteki tanım tarafından gölgelenmiş olduğu yeni bir leksikal kapsam başlatır.

```julia
x = 1
let x = 5
    @show x # 5
end
@show x # 1
```

Aşağıdaki örnekte, Julia'nın sözcüksel kapsam kullandığı için, `f` fonksiyonunun gövdesindeki `x` değişkeni, küresel kapsamda tanımlanan `x`'e atıfta bulunur ve bir `let` kapsamına girmek, `f`'nin gözlemlediği değeri değiştirmez.

```julia
x = 1
f() = @show x
let x = 5
    f() # 1
end
f() # 1
```

Artık bir `ScopedValue` kullanarak **dinamik** kapsamı kullanabiliriz.

```julia
using Base.ScopedValues

x = ScopedValue(1)
f() = @show x[]
with(x=>5) do
    f() # 5
end
f() # 1
```

Gözlemlenen `ScopedValue` değerinin programın yürütme yoluna bağlı olduğunu unutmayın.

Bir `const` değişkeninin bir kapsamlı değere işaret etmesi genellikle mantıklıdır ve bir `with` çağrısıyla birden fazla `ScopedValue`'nın değerini ayarlayabilirsiniz.

```julia
using Base.ScopedValues

f() = @show a[]
g() = @show b[]

const a = ScopedValue(1)
const b = ScopedValue(2)

f() # a[] = 1
g() # b[] = 2

# Enter a new dynamic scope and set value.
with(a => 3) do
    f() # a[] = 3
    g() # b[] = 2
    with(a => 4, b => 5) do
        f() # a[] = 4
        g() # b[] = 5
    end
    f() # a[] = 3
    g() # b[] = 2
end

f() # a[] = 1
g() # b[] = 2
```

`ScopedValues`, `with` makrosunun bir versiyonunu sağlar. `@with var=>val expr` ifadesi, `var`'ı `val` olarak ayarlayarak `expr`'yi yeni bir dinamik kapsamda değerlendirir. `@with var=>val expr`, `with(var=>val) do expr end` ile eşdeğerdir. Ancak, `with` sıfır argümanlı bir kapanış veya fonksiyon gerektirir, bu da ekstra bir çağrı çerçevesi ile sonuçlanır. Örnek olarak, aşağıdaki `f` fonksiyonunu düşünün:

```julia
using Base.ScopedValues
const a = ScopedValue(1)
f(x) = a[] + x
```

Eğer `f`'yi dinamik bir kapsamda `a`'yı `2` olarak ayarlamak istiyorsanız, `with` kullanabilirsiniz:

```julia
with(() -> f(10), a=>2)
```

Ancak, bu `f`'yi sıfır-argümanlı bir fonksiyonun içine sarmayı gerektirir. Ek çağrı çerçevesinden kaçınmak istiyorsanız, `@with` makrosunu kullanabilirsiniz:

```julia
@with a=>2 f(10)
```

!!! note
    Dinamik kapsamlar, görev oluşturma anında [`Task`](@ref)'lar tarafından miras alınır. Dinamik kapsamlar, `Distributed.jl` işlemleri aracılığıyla **yayılmaz**.


Aşağıdaki örnekte, bir görevi başlatmadan önce yeni bir dinamik kapsam açıyoruz. Ana görev ve iki çocuk görev, aynı anda aynı kapsamlı değerin bağımsız değerlerini gözlemliyor.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const scoped_val = ScopedValue(1)
@sync begin
    with(scoped_val => 2)
        @spawn @show scoped_val[] # 2
    end
    with(scoped_val => 3)
        @spawn @show scoped_val[] # 3
    end
    @show scoped_val[] # 1
end
```

Kapsamlı değerler bir kapsam boyunca sabittir, ancak bir kapsamlı değerde değişken durum saklayabilirsiniz. Sadece, küresel değişkenler için geçerli olan olağan uyarıların eşzamanlı programlama bağlamında geçerli olduğunu unutmayın.

Dikkat, kapsamlı değerlerde değişken duruma referanslar saklarken de gereklidir. Yeni bir dinamik kapsam girdiğinizde açıkça [unshare mutable state](@ref unshare_mutable_state) kullanmak isteyebilirsiniz.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# Example of using a mutable value wrongly
@sync begin
    # `Dict` is not thread-safe the usage below is invalid
    @spawn (sval_dict[][:a] = 3)
    @spawn (sval_dict[][:b] = 3)
end

@sync begin
    # If we instead pass a unique dictionary to each
    # task we can access the dictionaries race free.
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:a] = 3)
    end
    with(sval_dict => Dict()) do
        @spawn (sval_dict[][:b] = 3)
    end
end
```

## Example

Aşağıdaki örnekte, bir web uygulamasında bir izin kontrolü uygulamak için bir kapsamlı değer kullanıyoruz. İsteğin izinlerini belirledikten sonra, yeni bir dinamik kapsam girilir ve kapsamlı değer `LEVEL` ayarlanır. Uygulamanın diğer bölümleri kapsamlı değeri sorgulayabilir ve uygun değeri alır. Görev yerel depolama ve küresel değişkenler gibi diğer alternatifler bu tür bir yayılma için iyi bir şekilde uygun değildir; tek alternatifimiz, bir değeri tüm çağrı zinciri boyunca geçmek olacaktı.

```julia
using Base.ScopedValues

const LEVEL = ScopedValue(:GUEST)

function serve(request, response)
    level = isAdmin(request) ? :ADMIN : :GUEST
    with(LEVEL => level) do
        Threads.@spawn handle(request, response)
    end
end

function open(connection::Database)
    level = LEVEL[]
    if level !== :ADMIN
        error("Access disallowed")
    end
    # ... open connection
end

function handle(request, response)
    # ...
    open(Database(#=...=#))
    # ...
end
```

## Idioms

### [Unshare mutable state](@id unshare_mutable_state)

```julia
using Base.ScopedValues
import Base.Threads: @spawn

const sval_dict = ScopedValue(Dict())

# If you want to add new values to the dict, instead of replacing
# it, unshare the values explicitly. In this example we use `merge`
# to unshare the state of the dictionary in parent scope.
@sync begin
    with(sval_dict => merge(sval_dict[], Dict(:a => 10))) do
        @spawn @show sval_dict[][:a]
    end
    @spawn sval_dict[][:a] = 3 # Not a race since they are unshared.
end
```

### Scoped values as globals

Bir kapsamlı değerin değerine erişmek için, kapsamlı değerin kendisinin (leksikal) kapsamda olması gerekir. Bu, çoğu zaman kapsamlı değerleri sabit küresel değişkenler olarak kullanmak isteyeceğiniz anlamına gelir.

```julia
using Base.ScopedValues
const sval = ScopedValue(1)
```

Gerçekten de kapsamlı değerleri gizli fonksiyon argümanları olarak düşünebiliriz.

Bu, onların küresel olmayanlar olarak kullanılmasını engellemez.

```julia
using Base.ScopedValues
import Base.Threads: @spawn

function main()
    role = ScopedValue(:client)

    function launch()
        #...
        role[]
    end

    @with role => :server @spawn launch()
    launch()
end
```

Ama bu durumlarda işlev argümanını doğrudan geçmek daha basit olabilirdi.

### Very many ScopedValues

Eğer bir modül için birçok `ScopedValue` oluşturuyorsanız, bunları tutmak için özel bir yapı kullanmak daha iyi olabilir.

```julia
using Base.ScopedValues

Base.@kwdef struct Configuration
    color::Bool = false
    verbose::Bool = false
end

const CONFIG = ScopedValue(Configuration(color=true))

@with CONFIG => Configuration(color=CONFIG[].color, verbose=true) begin
    @show CONFIG[].color # true
    @show CONFIG[].verbose # true
end
```

## API docs

```@docs
Base.ScopedValues.ScopedValue
Base.ScopedValues.with
Base.ScopedValues.@with
Base.isassigned(::Base.ScopedValues.ScopedValue)
Base.ScopedValues.get
```

## Implementation notes and performance

`Scope`'lar kalıcı bir sözlük kullanır. Arama ve ekleme `O(log(32, n))`'dir, dinamik kapsam girişi sırasında küçük bir veri kopyalanır ve değişmeyen veriler diğer kapsamlar arasında paylaşılır.

`Scope` nesnesi kendisi kullanıcıya yönelik değildir ve gelecekteki bir Julia sürümünde değiştirilebilir.

## Design inspiration

Bu tasarım, [JEPS-429](https://openjdk.org/jeps/429) tarafından büyük ölçüde ilham alınarak oluşturulmuştur; bu da birçok Lisp lehçesindeki dinamik olarak kapsamlı serbest değişkenlerden esinlenmiştir. Özellikle Interlisp-D ve onun derin bağlama stratejisi.

Önceki tartışılan tasarım, [PEPS-567](https://peps.python.org/pep-0567/) gibi bağlam değişkenleri ve Julia'da [ContextVariablesX.jl](https://github.com/tkf/ContextVariablesX.jl) olarak uygulanmıştır.
