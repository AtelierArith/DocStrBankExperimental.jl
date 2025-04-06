```
remoteref_id(r::AbstractRemoteRef) -> RRID
```

`Future`s와 `RemoteChannel`s는 다음 필드로 식별됩니다:

  * `where` - 참조가 실제로 존재하는 기본 객체/저장소가 있는 노드를 나타냅니다.
  * `whence` - 원격 참조가 생성된 노드를 나타냅니다. 이는 참조된 기본 객체가 실제로 존재하는 노드와 다릅니다. 예를 들어, 마스터 프로세스에서 `RemoteChannel(2)`를 호출하면 `where` 값은 2이고 `whence` 값은 1이 됩니다.
  * `id`는 `whence`로 지정된 작업자에서 생성된 모든 참조에서 고유합니다.

함께 고려할 때, `whence`와 `id`는 모든 작업자에서 참조를 고유하게 식별합니다.

`remoteref_id`는 원격 참조의 `whence` 및 `id` 값을 래핑하는 `RRID` 객체를 반환하는 저수준 API입니다.
