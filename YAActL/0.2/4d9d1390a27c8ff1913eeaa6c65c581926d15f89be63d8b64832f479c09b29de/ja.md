```
Actor([lp::LinkParams], bhv::Function, args1...; kwargs...)
Actor(pid::Int, bhv::Function, args1...; kwargs...)
```

新しいアクターを作成します。返された自己に送信されたメッセージ `msg` をリッスンするタスクを開始し、各メッセージに対して `bhv(args1..., msg; kwargs...)` を実行します。アクターは [`Stop()`](@ref) が送信されると停止します。

# 引数

  * `[lp::LinkParams]`: アクターを作成するためのパラメータ、
  * `pid::Int`: アクターを作成するプロセス `pid`、これは `lp` でも指定できます、
  * `bhv`: アクターの動作を実装する関数、
  * `args1...`: `bhv` への最初の引数（可能な `msg` 引数なし）、
  * `kwargs...`: `bhv` へのキーワード引数。

# 戻り値

  * 作成されたアクターへの [`Link`](@ref)。

参照: [`LinkParams`](@ref)

# 例

```julia
julia> using YAActL, .Threads

julia> act1 = Actor(threadid)               # スレッドIDを返すアクターを開始
Channel{Message}(sz_max:32,sz_curr:0)

julia> call!(act1)                          # 呼び出す
1
```
