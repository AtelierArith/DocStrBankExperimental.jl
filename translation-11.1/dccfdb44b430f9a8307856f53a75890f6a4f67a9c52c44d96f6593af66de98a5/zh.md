```
ImmutableDict
```

`ImmutableDict` 是一个作为不可变链表实现的字典，适用于通过许多单独插入构建的小字典。请注意，无法删除一个值，尽管可以通过插入一个具有相同键的新值来部分覆盖和隐藏它。

```
ImmutableDict(KV::Pair)
```

为 `key => value` 对在 `ImmutableDict` 中创建一个新条目

  * 使用 `(key => value) in dict` 来查看这个特定组合是否在属性集中
  * 使用 `get(dict, key, default)` 来检索特定键的最新值
