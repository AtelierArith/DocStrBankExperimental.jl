```
invoke(f, argtypes::Type, args...; kwargs...)
```

Verilen genel işlev `f` için belirtilen türler `argtypes` ile belirtilen argümanlar `args` üzerinde eşleşen bir yöntemi çağırın ve anahtar kelime argümanları `kwargs` geçirin. `args` argümanları, `argtypes` içinde belirtilen türlerle uyumlu olmalıdır, yani dönüşüm otomatik olarak gerçekleştirilmez. Bu yöntem, en spesifik eşleşen yöntem dışında bir yöntemi çağırmaya olanak tanır; bu, daha genel bir tanımın davranışının açıkça gerektiği durumlarda yararlıdır (genellikle aynı işlevin daha spesifik bir yönteminin uygulanmasının bir parçası olarak).

Yazmadığınız işlevler için `invoke` kullanırken dikkatli olun. Verilen `argtypes` için hangi tanımın kullanıldığı, işlevin belirli `argtypes` ile çağrılmasının kamu API'sinin bir parçası olduğunu açıkça belirtmediği sürece bir uygulama ayrıntısıdır. Örneğin, aşağıdaki örnekte `f1` ve `f2` arasındaki değişiklik genellikle uyumlu olarak kabul edilir çünkü değişiklik, normal (non-`invoke`) çağrıda çağıran tarafından görünmez. Ancak, `invoke` kullanırsanız değişiklik görünür hale gelir.

# Örnekler

```jldoctest
julia> f(x::Real) = x^2;

julia> f(x::Integer) = 1 + invoke(f, Tuple{Real}, x);

julia> f(2)
5

julia> f1(::Integer) = Integer
       f1(::Real) = Real;

julia> f2(x::Real) = _f2(x)
       _f2(::Integer) = Integer
       _f2(_) = Real;

julia> f1(1)
Integer

julia> f2(1)
Integer

julia> invoke(f1, Tuple{Real}, 1)
Real

julia> invoke(f2, Tuple{Real}, 1)
Integer
```
