```
SharedArray{T}(dims::NTuple; init=false, pids=Int[])
SharedArray{T,N}(...)
```

비트 타입 `T`와 크기 `dims`의 `SharedArray`를 지정된 프로세스 `pids`에 걸쳐 생성합니다. 모든 프로세스는 동일한 호스트에 있어야 합니다. `N`이 `SharedArray{T,N}(dims)`를 호출하여 지정되면, `N`은 `dims`의 길이와 일치해야 합니다.

`pids`가 지정되지 않으면, 공유 배열은 현재 호스트의 모든 프로세스에 걸쳐 매핑되며, 마스터를 포함합니다. 그러나 `localindices`와 `indexpids`는 작업자 프로세스만 참조합니다. 이는 작업 분배 코드를 통해 마스터 프로세스가 드라이버 역할을 하면서 실제 계산을 위해 작업자를 사용할 수 있도록 합니다.

`init` 함수의 유형 `initfn(S::SharedArray)`가 지정되면, 참여하는 모든 작업자에서 호출됩니다.

공유 배열은 매핑을 생성한 노드에 `SharedArray` 객체에 대한 참조가 존재하는 한 유효합니다.

```
SharedArray{T}(filename::AbstractString, dims::NTuple, [offset=0]; mode=nothing, init=false, pids=Int[])
SharedArray{T,N}(...)
```

파일 `filename`에 의해 지원되는 `SharedArray`를 생성하며, 요소 타입 `T`(비트 타입이어야 함)와 크기 `dims`를 지정된 프로세스 `pids`에 걸쳐 생성합니다. 모든 프로세스는 동일한 호스트에 있어야 합니다. 이 파일은 호스트 메모리에 mmapped되며, 다음과 같은 결과를 초래합니다:

  * 배열 데이터는 이진 형식으로 표현되어야 합니다(예: CSV와 같은 ASCII 형식은 지원되지 않음)
  * 배열 값에 대한 변경(예: `A[3] = 0`)은 디스크의 값도 변경합니다.

`pids`가 지정되지 않으면, 공유 배열은 현재 호스트의 모든 프로세스에 걸쳐 매핑되며, 마스터를 포함합니다. 그러나 `localindices`와 `indexpids`는 작업자 프로세스만 참조합니다. 이는 작업 분배 코드를 통해 마스터 프로세스가 드라이버 역할을 하면서 실제 계산을 위해 작업자를 사용할 수 있도록 합니다.

`mode`는 `"r"`, `"r+"`, `"w+"`, 또는 `"a+"` 중 하나여야 하며, `filename`으로 지정된 파일이 이미 존재하는 경우 기본값은 `"r+"`이고, 존재하지 않는 경우는 `"w+"`입니다. `init` 함수의 유형 `initfn(S::SharedArray)`가 지정되면, 참여하는 모든 작업자에서 호출됩니다. 파일이 쓰기 가능하지 않은 경우 `init` 함수를 지정할 수 없습니다.

`offset`은 파일의 시작 부분에서 지정된 바이트 수를 건너뛰도록 허용합니다.
