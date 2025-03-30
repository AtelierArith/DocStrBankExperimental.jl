```
Stateful(itr)
```

有几种不同的方式来理解这个迭代器包装器：

1. 它提供了一个可变的包装器，围绕一个迭代器及其迭代状态。
2. 它将一个类似迭代器的抽象转变为一个类似 `Channel` 的抽象。
3. 它是一个迭代器，在生成一个项目时会变成它自己的剩余迭代器。

`Stateful` 提供了常规的迭代器接口。像其他可变迭代器（例如 [`Base.Channel`](@ref)）一样，如果迭代提前停止（例如在 [`for`](@ref) 循环中通过 [`break`](@ref)），可以通过继续迭代同一个迭代器对象从同一位置恢复迭代（相比之下，一个不可变的迭代器将从头开始）。

# 示例

```jldoctest
julia> a = Iterators.Stateful("abcdef");

julia> isempty(a)
false

julia> popfirst!(a)
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)

julia> collect(Iterators.take(a, 3))
3-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (category Ll: Letter, lowercase)
 'c': ASCII/Unicode U+0063 (category Ll: Letter, lowercase)
 'd': ASCII/Unicode U+0064 (category Ll: Letter, lowercase)

julia> collect(a)
2-element Vector{Char}:
 'e': ASCII/Unicode U+0065 (category Ll: Letter, lowercase)
 'f': ASCII/Unicode U+0066 (category Ll: Letter, lowercase)

julia> Iterators.reset!(a); popfirst!(a)
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)

julia> Iterators.reset!(a, "hello"); popfirst!(a)
'h': ASCII/Unicode U+0068 (category Ll: Letter, lowercase)
```

```jldoctest
julia> a = Iterators.Stateful([1,1,1,2,3,4]);

julia> for x in a; x == 1 || break; end

julia> peek(a)
3

julia> sum(a) # Sum the remaining elements
7
```
