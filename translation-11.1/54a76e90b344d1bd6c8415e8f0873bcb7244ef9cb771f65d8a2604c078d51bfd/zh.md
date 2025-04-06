```
print([to_toml::Function], io::IO [=stdout], data::AbstractDict; sorted=false, by=identity, inline_tables::IdSet{<:AbstractDict})
```

将 `data` 作为 TOML 语法写入流 `io`。如果关键字参数 `sorted` 设置为 `true`，则根据关键字参数 `by` 给定的函数对表进行排序。如果给定关键字参数 `inline_tables`，则它应该是一个应“内联”打印的表的集合。

支持以下数据类型：`AbstractDict`、`AbstractVector`、`AbstractString`、`Integer`、`AbstractFloat`、`Bool`、`Dates.DateTime`、`Dates.Time`、`Dates.Date`。请注意，整数和浮点数需要能够转换为 `Float64` 和 `Int64`。对于其他数据类型，请传递函数 `to_toml`，该函数接受数据类型并返回支持类型的值。
