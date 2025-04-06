```
verify_host(url::AbstractString, [transport::AbstractString]) :: Bool
```

Die Funktion `verify_host` informiert den Aufrufer darüber, ob die Identität eines Hosts bei der Kommunikation über sichere Transportprotokolle wie TLS oder SSH überprüft werden sollte. Das Argument `url` kann sein:

1. eine gültige URL, die mit `proto://` beginnt
2. ein `ssh`-Stil nackter Hostname oder ein Hostname, der mit `user@` vorangestellt ist
3. ein `scp`-Stil Host wie oben, gefolgt von `:` und einem Pfad

In jedem Fall wird der Hostname-Teil herausgefiltert und die Entscheidung, ob überprüft werden soll oder nicht, basiert ausschließlich auf dem Hostnamen, nicht auf anderen Aspekten der Eingabe-URL. Insbesondere spielt das Protokoll der URL keine Rolle (mehr dazu unten).

Das Argument `transport` gibt an, um welche Art von Transport es sich bei der Abfrage handelt. Die derzeit bekannten Werte sind `SSL`/`ssl` (Alias `TLS`/`tls`) und `SSH`/`ssh`. Wenn der Transport weggelassen wird, gibt die Abfrage nur dann `true` zurück, wenn der Hostname unabhängig vom Transport nicht überprüft werden sollte.

Der Hostname wird mit den Hostmustern in den relevanten Umgebungsvariablen abgeglichen, abhängig davon, ob `transport` angegeben ist und welchen Wert es hat:

  * `JULIA_NO_VERIFY_HOSTS` — Hosts, die für keinen Transport überprüft werden sollten
  * `JULIA_SSL_NO_VERIFY_HOSTS` — Hosts, die für SSL/TLS nicht überprüft werden sollten
  * `JULIA_SSH_NO_VERIFY_HOSTS` — Hosts, die für SSH nicht überprüft werden sollten
  * `JULIA_ALWAYS_VERIFY_HOSTS` — Hosts, die immer überprüft werden sollten

Die Werte jeder dieser Variablen sind eine durch Kommas getrennte Liste von Hostnamenmustern mit folgender Syntax — jedes Muster wird an `.` in Teile aufgeteilt, und jeder Teil muss eines der folgenden sein:

1. Ein literales Domainnamenkomponente, das aus einem oder mehreren ASCII-Buchstaben, Ziffern, Bindestrichen oder Unterstrichen besteht (technisch gesehen kein Teil eines legalen Hostnamens, wird aber manchmal verwendet). Eine literale Domainnamenkomponente passt nur zu sich selbst.
2. Ein `**`, das null oder mehr Domainnamenkomponenten übereinstimmt.
3. Ein `*`, das genau eine Domainnamenkomponente übereinstimmt.

Beim Abgleichen eines Hostnamens mit einer Mustervorlage in einer dieser Variablen wird der Hostname an `.` in Komponenten aufgeteilt, und diese Wortfolge wird mit dem Muster abgeglichen: Ein literales Muster passt genau zu einer Hostnamenkomponente mit diesem Wert; ein `*`-Muster passt genau zu einer Hostnamenkomponente mit beliebigem Wert; ein `**`-Muster passt zu beliebig vielen Hostnamenkomponenten. Zum Beispiel:

  * `**` passt zu jedem Hostnamen
  * `**.org` passt zu jedem Hostnamen in der Top-Level-Domain `.org`
  * `example.com` passt nur zu dem exakten Hostnamen `example.com`
  * `*.example.com` passt zu `api.example.com`, aber nicht zu `example.com` oder `v1.api.example.com`
  * `**.example.com` passt zu jeder Domain unter `example.com`, einschließlich `example.com` selbst, `api.example.com` und `v1.api.example.com`

```
