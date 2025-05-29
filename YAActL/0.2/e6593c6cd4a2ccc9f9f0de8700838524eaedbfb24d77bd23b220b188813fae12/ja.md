```
LinkParams(pid=myid(), size=32; taskref=nothing, spawn=false)
```

[`Actor`](@ref)を設定するためのパラメータ。

  * `pid::Int`: プロセス識別子,
  * `size::Int`: チャンネルバッファサイズ、`size ≥ 10`でなければならない,
  * `taskref::Union{Nothing, Ref{Task}}`: 作成されたタスクへの参照が必要な場合は、キーワード引数`taskref`を介して`Ref{Task}`オブジェクトを渡してください。
  * `spawn::Bool`: `spawn = true`の場合、作成されたタスクは別のスレッドで並行してスケジュールされる可能性があり、`Threads.@spawn`を介してタスクを作成するのと同等です。
