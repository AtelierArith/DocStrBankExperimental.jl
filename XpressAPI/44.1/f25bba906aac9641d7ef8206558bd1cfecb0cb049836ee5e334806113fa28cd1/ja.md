```
XPRS_SOLSTATUS
```

XPRSoptimizeで解決された最後の問題の解のステータスです。（整数）

値: 0 : `XPRS_SOLSTATUS_NOTFOUND` 解が利用できません。 1 : `XPRS_SOLSTATUS_OPTIMAL` 最適解が見つかりました。 2 : `XPRS_SOLSTATUS_FEASIBLE` 最適であることが証明されていない解が見つかりました。 3 : `XPRS_SOLSTATUS_INFEASIBLE` 解は存在しません。 4 : `XPRS_SOLSTATUS_UNBOUNDED` 問題は無限大です（実行可能な場合）。
