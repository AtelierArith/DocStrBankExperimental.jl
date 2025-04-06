```
arg_writers([ type = ArgWrite ]) do path::String, arg::Function
    ## 테스트 전 설정 ##
    @arg_test arg begin
        arg :: ArgWrite
        ## `arg`를 사용한 테스트 ##
    end
    ## 테스트 후 정리 ##
end
```

`arg_writers` 함수는 do 블록을 받아들이며, 이는 `arg_write`가 처리할 수 있는 각 테스트 작성자 유형에 대해 한 번 호출됩니다. 이때 임시(존재하지 않는) `path`와 다양한 쓰기 가능한 인수 유형으로 변환될 수 있는 `arg`가 사용됩니다. 선택적 `type` 인수가 주어지면, do 블록은 해당 유형의 인수를 생성하는 작성자에 대해서만 호출됩니다.

do 블록에 전달된 `arg`는 인수 값 자체가 아닙니다. 일부 테스트 인수 유형은 각 테스트 케이스에 대해 초기화 및 종료가 필요하기 때문입니다. 열린 파일 핸들 인수를 고려해 보십시오: 한 테스트에 사용한 후에는 다시 사용할 수 없습니다. 다음 테스트를 위해 파일을 닫고 다시 열어야 합니다. 이 함수 `arg`는 `@arg_test arg begin ... end`를 사용하여 `ArgWrite` 인스턴스로 변환될 수 있습니다.

또한 `arg_readers`와 같은 경로 이름을 사용하는 `arg_writers` 메서드도 있습니다:

```
arg_writers(path::AbstractString, [ type = ArgWrite ]) do arg::Function
    ## 테스트 전 설정 ##
    @arg_test arg begin
        # 여기서 `arg :: ArgWrite`
        ## `arg`를 사용한 테스트 ##
    end
    ## 테스트 후 정리 ##
end
```

이 메서드는 `tempname()`에 의해 생성된 경로 이름 대신 `path`를 지정해야 할 경우 유용합니다. `path`가 `arg_writers` 외부에서 전달되므로, 이 형태에서는 do 블록에 대한 인수가 아닙니다.
