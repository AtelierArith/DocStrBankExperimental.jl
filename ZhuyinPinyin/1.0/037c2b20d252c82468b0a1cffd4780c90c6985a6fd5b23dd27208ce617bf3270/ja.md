```
to_zhuyin(pinyin)
```

ソース文字列内の任意のピンインシーケンスをその注音符号の等価物に変換します。

## 例

```julia-repl
julia> to_zhuyin("lu4 shi1")
"ㄌㄨ4 ㄕ1"

julia> to_zhuyin("shou4 dao4 wei3 qu5")
"ㄕㄡ4 ㄉㄠ4 ㄨㄟ3 ㄑㄩ5"
```
