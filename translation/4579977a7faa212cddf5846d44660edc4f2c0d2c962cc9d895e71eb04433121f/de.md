```
mkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
mkpidlock(at::String, proc::Process; kwopts...)
```

Erstellt eine pidfile-Sperre für den Pfad "at" für den aktuellen Prozess oder den Prozess, der durch pid oder proc identifiziert wird. Kann eine Funktion annehmen, die einmal nach dem Sperren ausgeführt wird, zur Verwendung in `do`-Blöcken, nach denen die Sperre automatisch geschlossen wird. Wenn die Sperre fehlschlägt und `wait` falsch ist, wird ein Fehler ausgelöst.

Die Sperre wird entweder durch `close`, einen `finalizer` oder kurz nach dem Verlassen von `proc` freigegeben. Stellen Sie sicher, dass der Rückgabewert bis zum Ende des kritischen Abschnitts Ihres Programms lebendig bleibt, damit der `finalizer` ihn nicht vorzeitig zurückgewinnt.

Optionale Schlüsselwortargumente:

  * `mode`: Dateizugriffsmodus (modifiziert durch die Prozess-Umask). Standardmäßig auf weltweit lesbar.
  * `poll_interval`: Geben Sie die maximale Zeit zwischen den Versuchen an (wenn `watch_file` nicht funktioniert)
  * `stale_age`: Löschen Sie eine vorhandene pidfile (unter Ignorierung der Sperre), wenn sie älter ist als diese viele Sekunden, basierend auf ihrer mtime. Die Datei wird nicht gelöscht, bis sie 5x länger als dies ist, wenn die pid in der Datei zu erscheinen scheint, als könnte sie gültig sein. Oder 25x länger, wenn `refresh` auf 0 überschrieben wird, um das Aktualisieren der Sperre zu deaktivieren. Standardmäßig ist dies deaktiviert (`stale_age` = 0), aber ein typischer empfohlener Wert wäre etwa 3-5x eine geschätzte normale Abschlusszeit.
  * `refresh`: Hält eine Sperre davon ab, veraltet zu werden, indem die mtime in jedem Zeitintervall, das vergeht, aktualisiert wird. Standardmäßig ist dies auf `stale_age/2` eingestellt, was der empfohlene Wert ist.
  * `wait`: Wenn wahr, blockieren, bis wir die Sperre erhalten, wenn falsch, Fehler auslösen, wenn die Sperre fehlschlägt.
