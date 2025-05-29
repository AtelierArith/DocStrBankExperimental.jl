```
gradtape(f, args...; ctx=GradCtx(), seed=1)
gradtape!(tape::Tape; seed=1)
```

`tape[tape.resultid]` に対する `Input` ノードの勾配を計算してテープに記録します。詳細なAPIについては grad() を参照してください。
