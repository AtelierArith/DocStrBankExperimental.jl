```
two_qubit_depolarizing_channel(p::Real)
```

2量子ビットの脱偏極チャネルを作成します。これは `kron(single_qubit_depolarizing_channel(p), single_qubit_depolarizing_channel(p))` と同じではないことに注意してください。
