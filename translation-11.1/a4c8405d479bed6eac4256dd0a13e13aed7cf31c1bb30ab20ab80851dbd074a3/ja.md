```
poll_fd(fd, timeout_s::Real=-1; readable=false, writable=false)
```

ファイルディスクリプタ `fd` の読み取りまたは書き込みの可用性の変化を監視し、`timeout_s` 秒で指定されたタイムアウトを設定します。

キーワード引数は、どの読み取りおよび/または書き込みの状態を監視するかを決定します。少なくとも1つは `true` に設定する必要があります。

返される値は、ポーリングの結果を示すブール型フィールド `readable`、`writable`、および `timedout` を持つオブジェクトです。
