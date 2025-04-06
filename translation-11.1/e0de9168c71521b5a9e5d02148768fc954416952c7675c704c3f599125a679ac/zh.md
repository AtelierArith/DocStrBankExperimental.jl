```
empty(a::AbstractDict, [index_type=keytype(a)], [value_type=valtype(a)])
```

创建一个空的 `AbstractDict` 容器，可以接受类型为 `index_type` 的索引和类型为 `value_type` 的值。第二个和第三个参数是可选的，默认为输入的 `keytype` 和 `valtype`，分别。（如果只指定了两种类型中的一种，则假定为 `value_type`，而 `index_type` 默认为 `keytype(a)`）。

自定义的 `AbstractDict` 子类型可以选择最适合给定索引和值类型的特定字典类型，通过对三参数签名进行特化。默认情况下返回一个空的 `Dict`。
