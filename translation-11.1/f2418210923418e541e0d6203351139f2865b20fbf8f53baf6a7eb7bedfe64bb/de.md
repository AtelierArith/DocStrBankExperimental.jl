```
errno([code])
```

Holen Sie den Wert von `errno` der C-Bibliothek. Wenn ein Argument angegeben ist, wird es verwendet, um den Wert von `errno` zu setzen.

Der Wert von `errno` ist nur unmittelbar nach einem `ccall` zu einer C-Bibliotheksroutine gültig, die ihn setzt. Insbesondere können Sie `errno` nicht an der nächsten Eingabeaufforderung in einem REPL aufrufen, da zwischen den Eingabeaufforderungen viel Code ausgeführt wird.
