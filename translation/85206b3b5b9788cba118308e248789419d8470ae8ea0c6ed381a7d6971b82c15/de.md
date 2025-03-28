```
Downloader(; [ grace::Real = 30 ])
```

`Downloader`-Objekte werden verwendet, um einzelne `download`-Operationen durchzuführen. Verbindungen, Namensauflösungen und andere Ressourcen werden innerhalb eines `Downloader` geteilt. Diese Verbindungen und Ressourcen werden nach einer konfigurierbaren Grace-Periode (Standard: 30 Sekunden) bereinigt, nachdem etwas mit ihm heruntergeladen wurde, oder wenn er garbage collected wird, je nachdem, was zuerst eintritt. Wenn die Grace-Periode auf null gesetzt ist, werden alle Ressourcen sofort bereinigt, sobald keine laufenden Downloads mehr im Gange sind. Wenn die Grace-Periode auf `Inf` gesetzt ist, werden Ressourcen erst bereinigt, wenn der `Downloader` garbage collected wird.
