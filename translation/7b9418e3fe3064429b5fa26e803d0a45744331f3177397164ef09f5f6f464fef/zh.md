```
iterate(iter [, state]) -> Union{Nothing, Tuple{Any, Any}}
```

推进迭代器以获取下一个元素。如果没有剩余元素，则应返回 `nothing`。否则，应返回下一个元素和新的迭代状态的 2 元组。
