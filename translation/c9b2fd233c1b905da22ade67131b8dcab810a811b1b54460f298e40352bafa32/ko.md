```
instances(T::Type)
```

주어진 타입의 모든 인스턴스 컬렉션을 반환합니다. 주로 열거형 타입에 사용됩니다(참조: `@enum`).

# 예제

```jldoctest
julia> @enum Color red blue green

julia> instances(Color)
(red, blue, green)
```
