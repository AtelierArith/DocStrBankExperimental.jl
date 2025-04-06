```
SimpleLogger([stream,] min_level=Info)
```

Ein einfacher Logger zum Protokollieren aller Nachrichten mit einem Level größer oder gleich `min_level` an `stream`. Wenn der Stream geschlossen ist, werden Nachrichten mit einem Protokolllevel größer oder gleich `Warn` an `stderr` und darunter an `stdout` protokolliert.
