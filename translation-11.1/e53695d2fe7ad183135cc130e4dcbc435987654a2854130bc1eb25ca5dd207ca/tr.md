```
showerror(io, e)
```

Bir istisna nesnesinin `e` tanımlayıcı bir temsilini gösterir. Bu yöntem, [`throw`](@ref) çağrısından sonra istisnayı görüntülemek için kullanılır.

# Örnekler

```jldoctest
julia> struct MyException <: Exception
           msg::String
       end

julia> function Base.showerror(io::IO, err::MyException)
           print(io, "MyException: ")
           print(io, err.msg)
       end

julia> err = MyException("test exception")
MyException("test exception")

julia> sprint(showerror, err)
"MyException: test exception"

julia> throw(MyException("test exception"))
HATA: MyException: test exception
```
