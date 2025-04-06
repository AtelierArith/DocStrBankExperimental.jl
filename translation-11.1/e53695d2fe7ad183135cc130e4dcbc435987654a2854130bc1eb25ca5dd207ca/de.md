```
showerror(io, e)
```

Zeigt eine beschreibende Darstellung eines Ausnahmeobjekts `e`. Diese Methode wird verwendet, um die Ausnahme nach einem Aufruf von [`throw`](@ref) anzuzeigen.

# Beispiele

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
ERROR: MyException: test exception
```
