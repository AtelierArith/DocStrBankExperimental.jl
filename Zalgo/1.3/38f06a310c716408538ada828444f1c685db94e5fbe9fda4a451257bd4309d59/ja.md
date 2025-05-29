```
zalgo(str::String, upmarks = 1:4, middlemarks = 1:4,
    downmarks = 1:4, maxmarks = 6)
```

文字列 `str` の各文字に最大 `maxmarks` のダイアクリティックマークをランダムに追加します。`upmarks`、`middlemarks`、および `downmarks` の範囲は、その位置の文字に追加されるダイアクリティックマークの最小数と最大数を決定します。
