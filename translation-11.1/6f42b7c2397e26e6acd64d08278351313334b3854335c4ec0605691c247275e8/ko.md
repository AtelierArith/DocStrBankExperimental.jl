```
Profile.take_heap_snapshot(filepath::String, all_one::Bool=false, streaming=false)
Profile.take_heap_snapshot(all_one::Bool=false; dir::String, streaming=false)
```

힙의 스냅샷을 작성하여 Chrome Devtools Heap Snapshot 뷰어에서 기대하는 JSON 형식으로 파일(`$pid_$timestamp.heapsnapshot`)에 저장합니다. 기본적으로 현재 디렉토리에 저장되며(현재 디렉토리에 쓸 수 없는 경우 tempdir에 저장됨), 또는 주어진 경우 `dir`에 저장되거나 주어진 전체 파일 경로 또는 IO 스트림에 저장됩니다.

`all_one`이 true인 경우, 모든 객체의 크기를 1로 보고하여 쉽게 계산할 수 있도록 합니다. 그렇지 않으면 실제 크기를 보고합니다.

`streaming`이 true인 경우, 스냅샷 데이터를 네 개의 파일로 스트리밍하여 filepath를 접두사로 사용하여 전체 스냅샷을 메모리에 보관하지 않도록 합니다. 이 옵션은 메모리가 제한된 설정에서 사용해야 합니다. 이러한 파일은 Profile.HeapSnapshot.assemble_snapshot()을 호출하여 재조립할 수 있으며, 이는 오프라인에서 수행할 수 있습니다.

참고: 성능상의 이유로 streaming=true로 설정하는 것을 강력히 권장합니다. 부분에서 스냅샷을 재구성하려면 전체 스냅샷을 메모리에 보관해야 하므로, 스냅샷이 크면 처리 중에 메모리가 부족할 수 있습니다. 스트리밍을 사용하면 작업이 완료된 후 오프라인에서 스냅샷을 재구성할 수 있습니다. streaming=false(기본값, 이전 호환성을 위해)로 스냅샷을 수집하려고 시도하고 프로세스가 종료되면, 제공된 파일 경로와 동일한 디렉토리에 항상 부분이 저장되므로, `assemble_snapshot()`을 통해 나중에 스냅샷을 재구성할 수 있습니다.
