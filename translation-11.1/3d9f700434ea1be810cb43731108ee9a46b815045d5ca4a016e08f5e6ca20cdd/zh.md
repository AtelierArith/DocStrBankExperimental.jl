```
notify(condition, val=nothing; all=true, error=false)
```

唤醒等待条件的任务，并传递给它们 `val`。如果 `all` 为 `true`（默认值），则唤醒所有等待的任务，否则只唤醒一个。如果 `error` 为 `true`，则在被唤醒的任务中将传递的值作为异常抛出。

返回唤醒的任务数量。如果没有任务在 `condition` 上等待，则返回 0。
