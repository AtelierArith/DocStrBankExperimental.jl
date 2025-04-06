```
fullname(m::Module)
```

모듈의 완전한 이름을 기호의 튜플로 가져옵니다. 예를 들어,

# 예시

```jldoctest
julia> fullname(Base.Iterators)
(:Base, :Iterators)

julia> fullname(Main)
(:Main,)
```
