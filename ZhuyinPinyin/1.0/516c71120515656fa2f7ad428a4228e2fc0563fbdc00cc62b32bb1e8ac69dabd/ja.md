```
to_pinyin(zhuyin)
```

ソース文字列内のすべての注音シーケンスをそのピンインの同等物に変換します。

## 例

```julia-repl
julia> to_pinyin("ㄨ ㄑㄧ ㄇㄚ ㄏㄟ")
"wu qi ma hei"

julia> to_pinyin("ㄏㄨ2 ㄕㄨㄛ1 ㄅㄚ1 ㄉㄠ4")
"hu2 shuo1 ba1 dao4"
```
