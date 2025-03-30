```
매크로
```

`매크로`는 생성된 코드를 프로그램에 삽입하는 방법을 정의합니다. 매크로는 인수 표현식의 시퀀스를 반환된 표현식에 매핑하며, 결과 표현식은 매크로가 호출된 지점에서 프로그램에 직접 대체됩니다. 매크로는 [`eval`](@ref Main.eval)을 호출하지 않고 생성된 코드를 실행하는 방법이며, 생성된 코드는 단순히 주변 프로그램의 일부가 됩니다. 매크로 인수에는 표현식, 리터럴 값 및 기호가 포함될 수 있습니다. 매크로는 가변 개수의 인수(varargs)에 대해 정의할 수 있지만, 키워드 인수는 허용하지 않습니다. 모든 매크로는 또한 암묵적으로 `__source__` 인수를 전달받으며, 이는 매크로가 호출된 줄 번호와 파일 이름을 포함하고, `__module__`은 매크로가 확장되는 모듈입니다.

매크로 작성 방법에 대한 자세한 정보는 [메타프로그래밍](@ref) 매뉴얼 섹션을 참조하십시오.

# 예제

```jldoctest
julia> macro sayhello(name)
           return :( println("Hello, ", $name, "!") )
       end
@sayhello (매크로 1개의 메서드가 있음)

julia> @sayhello "Charlie"
Hello, Charlie!

julia> macro saylots(x...)
           return :( println("Say: ", $(x...)) )
       end
@saylots (매크로 1개의 메서드가 있음)

julia> @saylots "hey " "there " "friend"
Say: hey there friend
```
