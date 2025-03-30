```
asyncmap(f, c...; ntasks=0, batch_size=nothing)
```

여러 개의 동시 작업을 사용하여 컬렉션(또는 여러 개의 동일 길이 컬렉션)에 대해 `f`를 매핑합니다. 여러 컬렉션 인수가 있는 경우, `f`는 요소별로 적용됩니다.

`ntasks`는 동시에 실행할 작업의 수를 지정합니다. 컬렉션의 길이에 따라 `ntasks`가 지정되지 않은 경우, 최대 100개의 작업이 동시 매핑에 사용됩니다.

`ntasks`는 또한 인수가 없는 함수로 지정할 수 있습니다. 이 경우, 각 요소를 처리하기 전에 병렬로 실행할 작업의 수가 확인되며, `ntasks_func`의 값이 현재 작업 수보다 크면 새로운 작업이 시작됩니다.

`batch_size`가 지정되면 컬렉션은 배치 모드로 처리됩니다. 이 경우 `f`는 인수 튜플의 `Vector`를 받아들이고 결과의 벡터를 반환해야 하는 함수여야 합니다. 입력 벡터는 `batch_size` 또는 그보다 짧은 길이를 가집니다.

다음 예제는 매핑 함수가 실행되는 작업의 `objectid`를 반환하여 서로 다른 작업에서의 실행을 강조합니다.

먼저, `ntasks`가 정의되지 않은 경우 각 요소는 다른 작업에서 처리됩니다.

```
julia> tskoid() = objectid(current_task());

julia> asyncmap(x->tskoid(), 1:5)
5-element Array{UInt64,1}:
 0x6e15e66c75c75853
 0x440f8819a1baa682
 0x9fb3eeadd0c83985
 0xebd3e35fe90d4050
 0x29efc93edce2b961

julia> length(unique(asyncmap(x->tskoid(), 1:5)))
5
```

`ntasks=2`인 경우 모든 요소는 2개의 작업에서 처리됩니다.

```
julia> asyncmap(x->tskoid(), 1:5; ntasks=2)
5-element Array{UInt64,1}:
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94
 0xa23d2f80cd7cf157
 0x027ab1680df7ae94

julia> length(unique(asyncmap(x->tskoid(), 1:5; ntasks=2)))
2
```

`batch_size`가 정의된 경우, 매핑 함수는 인수 튜플의 배열을 받아들이고 결과의 배열을 반환하도록 변경해야 합니다. 이를 달성하기 위해 수정된 매핑 함수에서 `map`이 사용됩니다.

```
julia> batch_func(input) = map(x->string("args_tuple: ", x, ", element_val: ", x[1], ", task: ", tskoid()), input)
batch_func (generic function with 1 method)

julia> asyncmap(batch_func, 1:5; ntasks=2, batch_size=2)
5-element Array{String,1}:
 "args_tuple: (1,), element_val: 1, task: 9118321258196414413"
 "args_tuple: (2,), element_val: 2, task: 4904288162898683522"
 "args_tuple: (3,), element_val: 3, task: 9118321258196414413"
 "args_tuple: (4,), element_val: 4, task: 4904288162898683522"
 "args_tuple: (5,), element_val: 5, task: 9118321258196414413"
```
