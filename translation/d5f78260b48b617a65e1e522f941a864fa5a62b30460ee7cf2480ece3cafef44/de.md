```
start_worker([out::IO=stdout], cookie::AbstractString=readline(stdin); close_stdin::Bool=true, stderr_to_stdout::Bool=true)
```

`start_worker` ist eine interne Funktion, die den Standard-Einstiegspunkt für Arbeitsprozesse darstellt, die sich über TCP/IP verbinden. Sie richtet den Prozess als Julia-Cluster-Arbeiter ein.

Host:Port-Informationen werden in den Stream `out` geschrieben (standardmäßig stdout).

Die Funktion liest das Cookie von stdin, falls erforderlich, und hört auf einem freien Port (oder, falls angegeben, dem Port in der `--bind-to`-Befehlszeilenoption) und plant Aufgaben zur Verarbeitung eingehender TCP-Verbindungen und -Anfragen. Sie schließt auch (optional) stdin und leitet stderr an stdout um.

Sie gibt nichts zurück.
