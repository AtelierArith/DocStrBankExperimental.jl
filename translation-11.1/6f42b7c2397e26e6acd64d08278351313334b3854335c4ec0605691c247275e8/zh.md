```
Profile.take_heap_snapshot(filepath::String, all_one::Bool=false, streaming=false)
Profile.take_heap_snapshot(all_one::Bool=false; dir::String, streaming=false)
```

写入堆的快照，格式为 Chrome Devtools Heap Snapshot viewer 所期望的 JSON 格式（.heapsnapshot 扩展名），默认情况下将其写入当前目录中的文件（`$pid_$timestamp.heapsnapshot`）（如果当前目录不可写，则写入 tempdir），或者写入给定的 `dir`，或者给定的完整文件路径，或 IO 流。

如果 `all_one` 为 true，则将每个对象的大小报告为 1，以便于计数。否则，报告实际大小。

如果 `streaming` 为 true，我们将把快照数据流式输出到四个文件中，使用 filepath 作为前缀，以避免将整个快照保存在内存中。此选项应在内存受限的情况下使用。这些文件可以通过调用 Profile.HeapSnapshot.assemble_snapshot() 进行重新组装，这可以在离线时完成。

注意：我们强烈建议出于性能原因将 streaming=true。根据部分重建快照需要将整个快照保存在内存中，因此如果快照很大，处理时可能会耗尽内存。流式传输允许您在工作负载完成后离线重建快照。如果您尝试在 streaming=false（默认情况下，为了向后兼容）时收集快照，并且您的进程被终止，请注意，这将始终将部分保存到您提供的文件路径相同的目录中，因此您仍然可以通过 `assemble_snapshot()` 在事后重建快照。
