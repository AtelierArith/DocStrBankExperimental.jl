```
showerror(io, e)
```

Affiche une représentation descriptive d'un objet d'exception `e`. Cette méthode est utilisée pour afficher l'exception après un appel à [`throw`](@ref).

# Exemples

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
