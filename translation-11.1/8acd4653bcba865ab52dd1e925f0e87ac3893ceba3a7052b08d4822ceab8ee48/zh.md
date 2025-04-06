```
annotate!(str::AnnotatedString, [range::UnitRange{Int}], label::Symbol, value)
annotate!(str::SubString{AnnotatedString}, [range::UnitRange{Int}], label::Symbol, value)
```

用带标签的值（`label` => `value`）注释`str`的`range`（或整个字符串）。要删除现有的`label`注释，请使用值`nothing`。

注释应用于`str`的顺序在语义上是有意义的，如[`AnnotatedString`](@ref)中所述。
