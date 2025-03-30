```
indexpids(S::SharedArray)
```

返回当前工作者在映射 `SharedArray` 的工作者列表中的索引（即在 `procs(S)` 返回的相同列表中），如果 `SharedArray` 没有在本地映射，则返回 0。
