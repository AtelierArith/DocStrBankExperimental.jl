```
module
```

`module`는 [`Module`](@ref)를 선언하며, 이는 별도의 전역 변수 작업 공간입니다. 모듈 내에서는 다른 모듈에서 어떤 이름이 보이는지를 제어할 수 있으며(가져오기를 통해), 자신의 이름 중 어떤 것이 공개될 것인지(내보내기 및 공개를 통해)를 지정할 수 있습니다. 모듈을 사용하면 다른 사람의 코드와 함께 사용할 때 이름 충돌에 대해 걱정하지 않고 최상위 정의를 만들 수 있습니다. 더 많은 세부정보는 [모듈에 대한 매뉴얼 섹션](@ref modules)을 참조하십시오.

# 예제

```julia
module Foo
import Base.show
export MyType, foo

struct MyType
    x
end

bar(x) = 2x
foo(a::MyType) = bar(a.x) + 1
show(io::IO, a::MyType) = print(io, "MyType $(a.x)")
end
```
