```
modül
```

`modül`, ayrı bir global değişken çalışma alanı olan bir [`Modül`](@ref) tanımlar. Bir modül içinde, diğer modüllerden hangi isimlerin görünür olduğunu kontrol edebilir (içe aktarma yoluyla) ve kendi isimlerinizin hangilerinin kamuya açık olduğunu belirtebilirsiniz ( `export` ve `public` aracılığıyla). Modüller, kodunuzun başka birinin koduyla birlikte kullanıldığında isim çakışmalarından endişe etmeden üst düzey tanımlar oluşturmanıza olanak tanır. Daha fazla ayrıntı için [modüllerle ilgili kılavuz bölümüne](@ref modules) bakın.

# Örnekler

```julia
modül Foo
import Base.show
export MyType, foo

struct MyType
    x
end

bar(x) = 2x
foo(a::MyType) = bar(a.x) + 1
show(io::IO, a::MyType) = print(io, "MyType $(a.x)")
end
```
