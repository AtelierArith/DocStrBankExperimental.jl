```
displayable(mime) -> Bool
displayable(d::AbstractDisplay, mime) -> Bool
```

与えられた `mime` タイプ（文字列）が、現在の表示スタック内のいずれかの表示によって表示可能か、または第二のバリアントで表示 `d` によって特に表示可能かを示すブール値を返します。
