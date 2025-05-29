```
to_pinyin(zhuyin)
```

Convert any zhuyin sequences in the source string to its pinyin equivalent.

## Examples

```julia-repl
julia> to_pinyin("ㄨ ㄑㄧ ㄇㄚ ㄏㄟ")
"wu qi ma hei"

julia> to_pinyin("ㄏㄨ2 ㄕㄨㄛ1 ㄅㄚ1 ㄉㄠ4")
"hu2 shuo1 ba1 dao4"
```
