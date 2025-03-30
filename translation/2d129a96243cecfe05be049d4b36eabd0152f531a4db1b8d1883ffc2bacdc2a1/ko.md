```
finish(ts::AbstractTestSet)
```

주어진 테스트 세트에 필요한 최종 처리를 수행합니다. 이는 테스트 블록이 실행된 후 `@testset` 인프라에 의해 호출됩니다.

사용자 정의 `AbstractTestSet` 하위 유형은 테스트 결과 트리에 자신을 추가하기 위해 부모에게 `record`를 호출해야 합니다(부모가 있는 경우). 이는 다음과 같이 구현될 수 있습니다:

```julia
if get_testset_depth() != 0
    # 이 테스트 세트를 부모 테스트 세트에 연결합니다
    parent_ts = get_testset()
    record(parent_ts, self)
    return self
end
```
