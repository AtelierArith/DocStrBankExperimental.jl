```
fullname(m::Module)
```

获取模块的完全限定名称，返回一个符号元组。例如，

# 示例

```jldoctest
julia> fullname(Base.Iterators)
(:Base, :Iterators)

julia> fullname(Main)
(:Main,)
```
