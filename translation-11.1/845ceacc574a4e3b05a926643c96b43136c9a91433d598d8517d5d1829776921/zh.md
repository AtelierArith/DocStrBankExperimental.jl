```
readdlm(source, delim::AbstractChar, eol::AbstractChar; options...)
```

如果所有数据都是数字，结果将是一个数字数组。如果某些元素无法解析为数字，则返回一个包含数字和字符串的异构数组。
