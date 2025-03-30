```
Stateful(itr)
```

이 반복자 래퍼에 대해 생각할 수 있는 몇 가지 방법이 있습니다:

1. 반복자와 그 반복 상태에 대한 가변 래퍼를 제공합니다.
2. 반복자와 유사한 추상화를 `Channel`과 유사한 추상화로 변환합니다.
3. 항목이 생성될 때마다 자신의 나머지 반복자가 되도록 변형되는 반복자입니다.

`Stateful`은 일반적인 반복자 인터페이스를 제공합니다. 다른 가변 반복자(예: [`Base.Channel`](@ref))와 마찬가지로, 반복이 조기에 중단되면(예: [`for`](@ref) 루프에서 [`break`](@ref)로) 동일한 반복자 객체를 계속 반복하여 동일한 지점에서 반복을 재개할 수 있습니다(대조적으로, 불변 반복자는 처음부터 다시 시작합니다).

# 예제

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

julia> sum(a) # 남은 요소의 합계
7
```
