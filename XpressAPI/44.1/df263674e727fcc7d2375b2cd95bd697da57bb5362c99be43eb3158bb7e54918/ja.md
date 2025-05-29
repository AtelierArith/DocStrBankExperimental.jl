```
XPRS_MIPABSGAPNOTIFYBOUND
```

分枝限定法: `gapnotify` コールバックが XPRSaddcbgapnotify を使用して設定されている場合、このコールバックは、最良の境界が設定した `MIPRELGAPNOTIFYBOUND` 制御の値に達するか超えたときにツリー探索中にトリガーされます。(double)

デフォルト値: `1.0E+20` (最小化問題の場合); `-1.0E+20` (最大化問題の場合)

ドメイン: [-1E+40,+1E+40]
