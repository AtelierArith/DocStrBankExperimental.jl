```
print([io::IO = stdout,] [data::Vector = fetch()], [lidict::Union{LineInfoDict, LineInfoFlatDict} = getdict(data)]; kwargs...)
```

`io`にプロファイリング結果を出力します（デフォルトは`stdout`）。`data`ベクターを提供しない場合、蓄積されたバックトレースの内部バッファが使用されます。

キーワード引数は任意の組み合わせが可能です：

  * `format` – バックトレースがツリー構造を示すインデント付き（デフォルト、`:tree`）またはインデントなし（`:flat`）で印刷されるかどうかを決定します。
  * `C` – `true`の場合、CおよびFortranコードからのバックトレースが表示されます（通常は除外されます）。
  * `combine` – `true`（デフォルト）の場合、同じコード行に対応する命令ポインタがマージされます。
  * `maxdepth` – `:tree`形式で`maxdepth`より深い深さを制限します。
  * `sortedby` – `:flat`形式での順序を制御します。`:filefuncline`（デフォルト）はソース行でソートし、`:count`は収集されたサンプルの数の順にソートし、`:overhead`は各関数によって発生したサンプルの数でソートします。
  * `groupby` – タスクとスレッドのグループ化を制御します。オプションは`:none`（デフォルト）、`:thread`、`:task`、`[:thread, :task]`、または`[:task, :thread]`で、最後の2つはネストされたグループ化を提供します。
  * `noisefloor` – サンプルのヒューリスティックノイズフロアを超えるフレームを制限します（`:tree`形式にのみ適用されます）。これに対して試すべき推奨値は2.0です（デフォルトは0）。このパラメータは、`n <= noisefloor * √N`を満たすサンプルを隠します。ここで、`n`はこの行のサンプル数、`N`は呼び出し元のサンプル数です。
  * `mincount` – 出力を`mincount`回以上の出現がある行のみに制限します。
  * `recur` – `:tree`形式での再帰処理を制御します。`:off`（デフォルト）はツリーを通常通り印刷します。`:flat`は再帰を圧縮し（ipによって）、自己再帰をイテレータに変換した場合の近似効果を示します。`:flatc`は同様のことを行いますが、Cフレームの圧縮も含まれます（`jl_apply`周辺で奇妙な動作をする可能性があります）。
  * `threads::Union{Int,AbstractVector{Int}}` – レポートに含めるスナップショットを取得するスレッドを指定します。これは、サンプルが収集されるスレッドを制御するものではありません（別のマシンで収集された可能性もあります）。
  * `tasks::Union{Int,AbstractVector{Int}}` – レポートに含めるスナップショットを取得するタスクを指定します。これは、サンプルが収集されるタスクを制御するものではありません。

!!! compat "Julia 1.8"
    `groupby`、`threads`、および`tasks`キーワード引数はJulia 1.8で導入されました。


!!! note
    Windowsでのプロファイリングはメインスレッドに制限されています。他のスレッドはサンプリングされておらず、レポートには表示されません。

