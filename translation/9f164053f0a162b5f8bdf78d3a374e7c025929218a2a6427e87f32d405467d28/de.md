# Using Valgrind with Julia

[Valgrind](https://valgrind.org/) ist ein Werkzeug zur Speicher-Debugging, zur Erkennung von Speicherlecks und zur Profilerstellung. Dieser Abschnitt beschreibt Dinge, die man beachten sollte, wenn man Valgrind verwendet, um Speicherprobleme mit Julia zu debuggen.

## General considerations

Standardmäßig geht Valgrind davon aus, dass es keinen selbstmodifizierenden Code in den Programmen gibt, die es ausführt. Diese Annahme funktioniert in den meisten Fällen gut, schlägt jedoch miserabel bei einem Just-in-Time-Compiler wie `julia`. Aus diesem Grund ist es entscheidend, `--smc-check=all-non-file` an `valgrind` zu übergeben, andernfalls kann der Code abstürzen oder sich unerwartet verhalten (oft auf subtile Weise).

In einigen Fällen kann es hilfreich sein, `julia` mit deaktivierten Speicherpools zu kompilieren, um Speicherfehler besser zu erkennen, wenn man Valgrind verwendet. Das Kompilierungsflag `MEMDEBUG` deaktiviert die Speicherpools in Julia, und `MEMDEBUG2` deaktiviert die Speicherpools in FemtoLisp. Um `julia` mit beiden Flags zu bauen, fügen Sie die folgende Zeile zu `Make.user` hinzu:

```make
CFLAGS = -DMEMDEBUG -DMEMDEBUG2
```

Ein weiterer Punkt, den man beachten sollte: Wenn Ihr Programm mehrere Arbeitsprozesse verwendet, möchten Sie wahrscheinlich, dass alle diese Arbeitsprozesse unter Valgrind ausgeführt werden, nicht nur der Elternprozess. Um dies zu tun, übergeben Sie `--trace-children=yes` an `valgrind`.

Noch etwas zu beachten: Wenn bei der Verwendung von `valgrind` Fehler mit `Unable to find compatible target in system image` auftreten, versuchen Sie, das sysimage mit dem Ziel `generic` neu zu erstellen oder Julia mit `JULIA_CPU_TARGET=generic` zu kompilieren.

## Suppressions

Valgrind zeigt typischerweise während seiner Ausführung falsche Warnungen an. Um die Anzahl solcher Warnungen zu reduzieren, hilft es, Valgrind eine [suppressions file](https://valgrind.org/docs/manual/manual-core.html#manual-core.suppress) bereitzustellen. Eine Beispielunterdrückungsdatei ist im Julia-Quellcode-Vertrieb unter `contrib/valgrind-julia.supp` enthalten.

Die Unterdrückungsdatei kann aus dem `julia/` Quellverzeichnis wie folgt verwendet werden:

```
$ valgrind --smc-check=all-non-file --suppressions=contrib/valgrind-julia.supp ./julia progname.jl
```

Alle angezeigten Speicherfehler sollten entweder als Fehler gemeldet oder als zusätzliche Unterdrückungen beigetragen werden. Beachten Sie, dass einige Versionen von Valgrind [shipped with insufficient default suppressions](https://github.com/JuliaLang/julia/issues/8314#issuecomment-55766210) sind, sodass dies möglicherweise ein Punkt ist, den Sie vor der Einreichung von Fehlern berücksichtigen sollten.

## Running the Julia test suite under Valgrind

Es ist möglich, die gesamte Julia-Test-Suite unter Valgrind auszuführen, aber es dauert ziemlich lange (typischerweise mehrere Stunden). Um dies zu tun, führen Sie den folgenden Befehl im Verzeichnis `julia/test/` aus:

```
valgrind --smc-check=all-non-file --trace-children=yes --suppressions=$PWD/../contrib/valgrind-julia.supp ../julia runtests.jl all
```

Wenn Sie einen Bericht über "definitive" Speicherlecks sehen möchten, übergeben Sie die Flags `--leak-check=full --show-leak-kinds=definite` an `valgrind`.

## Additional spurious warnings

Dieser Abschnitt behandelt Valgrind-Warnungen, die nicht zur Unterdrückungsdatei hinzugefügt werden können, aber dennoch sicher ignoriert werden können.

### Unhandled rr system calls

Valgrind wird eine Warnung ausgeben, wenn es auf eines der [system calls that are specific to rr](https://github.com/rr-debugger/rr/blob/master/src/preload/rrcalls.h), das [Record and Replay Framework](https://rr-project.org/) stößt. Insbesondere wird eine Warnung über einen nicht behandelten `1008` Syscall angezeigt, wenn Julia versucht zu erkennen, ob es unter rr läuft:

```
--xxxxxx-- WARNING: unhandled amd64-linux syscall: 1008
--xxxxxx-- You may be able to write your own handler.
--xxxxxx-- Read the file README_MISSING_SYSCALL_OR_IOCTL.
--xxxxxx-- Nevertheless we consider this a bug.  Please report
--xxxxxx-- it at http://valgrind.org/support/bug_reports.html.
```

Dieses Problem [has been reported](https://bugs.kde.org/show_bug.cgi?id=446401) an die Valgrind-Entwickler, wie sie es angefordert haben.

## Caveats

Valgrind derzeit [does not support multiple rounding modes](https://bugs.kde.org/show_bug.cgi?id=136779), sodass Code, der den Rundungsmodus anpasst, sich unter Valgrind anders verhält.

Im Allgemeinen, wenn Sie nach dem Setzen von `--smc-check=all-non-file` feststellen, dass sich Ihr Programm unter Valgrind anders verhält, kann es hilfreich sein, `--tool=none` an `valgrind` zu übergeben, während Sie weiter untersuchen. Dies aktiviert die minimale Valgrind-Mechanik, läuft jedoch auch viel schneller, als wenn der vollständige Speicherprüfer aktiviert ist.
