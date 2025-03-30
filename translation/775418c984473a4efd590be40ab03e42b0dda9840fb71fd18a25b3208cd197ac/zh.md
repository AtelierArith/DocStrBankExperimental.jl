```
graphemes(s::AbstractString) -> GraphemeIterator
```

返回一个迭代器，该迭代器遍历字符串 `s` 中对应于扩展字形的子字符串，按照 Unicode UAX #29 的定义。（大致来说，这些是用户所感知的单个字符，即使它们可能包含多个代码点；例如，一个字母与一个重音符号组合在一起是一个单一的字形。）
