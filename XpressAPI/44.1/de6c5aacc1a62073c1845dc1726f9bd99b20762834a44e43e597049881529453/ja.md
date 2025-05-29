```
XPRS_IISSOLSTATUS
```

IISソリューションステータス。（整数）

値：0 : 未開始（`XPRS_IIS_UNSTARTED`）、通常はライセンスまたは入力エラーによる。1 : 実現可能（`XPRS_IIS_FEASIBLE`）、したがってIISは生成できない。2 : 完了（`XPRS_IIS_COMPLETED`）；これが通常の終了です。IISセットの数はNUMIIS属性を通じて照会できます。3 : 未完了（`XPRS_IIS_UNFINISHED`）、時間制限に達したか、ユーザーの中断によるものです。このステータスでIIS手続きが終了すると、最後のIISセットは簡約不可能である可能性があります。
