```
arg_readers(arg :: AbstractString, [ type = ArgRead ]) do arg::Function
    ## 사전 테스트 설정 ##
    @arg_test arg begin
        arg :: ArgRead
        ## `arg`를 사용한 테스트 ##
    end
    ## 사후 테스트 정리 ##
end
```

`arg_readers` 함수는 읽을 경로와 단일 인수 do 블록을 받아들이며, 이는 `arg_read`가 처리할 수 있는 각 테스트 리더 유형에 대해 한 번 호출됩니다. 선택적 `type` 인수가 주어지면 do 블록은 해당 유형의 인수를 생성하는 리더에 대해서만 호출됩니다.

do 블록에 전달된 `arg`는 인수 값 자체가 아닙니다. 일부 테스트 인수 유형은 각 테스트 케이스에 대해 초기화 및 종료가 필요하기 때문입니다. 열린 파일 핸들 인수를 고려해 보십시오: 한 테스트에 사용한 후에는 다시 사용할 수 없습니다. 다음 테스트를 위해 파일을 닫고 다시 열어야 합니다. 이 함수 `arg`는 `@arg_test arg begin ... end`를 사용하여 `ArgRead` 인스턴스로 변환될 수 있습니다.
