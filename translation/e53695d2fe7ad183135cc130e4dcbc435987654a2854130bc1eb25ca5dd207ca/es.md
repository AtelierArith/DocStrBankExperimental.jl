```
showerror(io, e)
```

Muestra una representación descriptiva de un objeto de excepción `e`. Este método se utiliza para mostrar la excepción después de una llamada a [`throw`](@ref).

# Ejemplos

```jldoctest
julia> struct MyException <: Exception
           msg::String
       end

julia> function Base.showerror(io::IO, err::MyException)
           print(io, "MyException: ")
           print(io, err.msg)
       end

julia> err = MyException("excepción de prueba")
MyException("excepción de prueba")

julia> sprint(showerror, err)
"MyException: excepción de prueba"

julia> throw(MyException("excepción de prueba"))
ERROR: MyException: excepción de prueba
```
