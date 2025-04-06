```
showerror(io, e)
```

예외 객체 `e`의 설명적인 표현을 보여줍니다. 이 메서드는 [`throw`](@ref) 호출 후 예외를 표시하는 데 사용됩니다.

# 예제

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
