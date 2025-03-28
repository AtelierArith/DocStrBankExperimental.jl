# Running External Programs

Julia leiht sich die Backtick-Notation für Befehle aus der Shell, Perl und Ruby. Allerdings bedeutet das Schreiben

```jldoctest
julia> `echo hello`
`echo hello`
```

unterscheidet sich in mehreren Aspekten vom Verhalten in verschiedenen Shells, Perl oder Ruby:

  * Statt den Befehl sofort auszuführen, erstellen Backticks ein [`Cmd`](@ref) Objekt, um den Befehl darzustellen. Sie können dieses Objekt verwenden, um den Befehl über Pipes mit anderen zu verbinden, [`run`](@ref) es und [`read`](@ref) oder [`write`](@ref) damit.
  * Wenn der Befehl ausgeführt wird, erfasst Julia seine Ausgabe nicht, es sei denn, Sie arrangieren dies speziell. Stattdessen geht die Ausgabe des Befehls standardmäßig an [`stdout`](@ref), wie es bei dem `system`-Aufruf von `libc` der Fall wäre.
  * Der Befehl wird niemals mit einer Shell ausgeführt. Stattdessen analysiert Julia die Befehlsyntax direkt, interpoliert Variablen angemessen und trennt die Wörter wie die Shell, wobei die Shell-Zitier-Syntax respektiert wird. Der Befehl wird als unmittelbarer Kindprozess von `julia` ausgeführt, unter Verwendung von `fork`- und `exec`-Aufrufen.

!!! note
    Die folgenden Annahmen gelten für eine Posix-Umgebung wie unter Linux oder MacOS. Unter Windows sind viele ähnliche Befehle, wie `echo` und `dir`, keine externen Programme, sondern sind stattdessen in die Shell `cmd.exe` selbst integriert. Eine Möglichkeit, diese Befehle auszuführen, besteht darin, `cmd.exe` aufzurufen, zum Beispiel `cmd /C echo hello`. Alternativ kann Julia in einer Posix-Umgebung wie Cygwin ausgeführt werden.


Hier ist ein einfaches Beispiel für das Ausführen eines externen Programms:

```jldoctest
julia> mycommand = `echo hello`
`echo hello`

julia> typeof(mycommand)
Cmd

julia> run(mycommand);
hello
```

Der `hello` ist die Ausgabe des `echo`-Befehls, der an [`stdout`](@ref) gesendet wird. Wenn der externe Befehl nicht erfolgreich ausgeführt werden kann, wirft die Methode run eine [`ProcessFailedException`](@ref).

Wenn Sie die Ausgabe des externen Befehls lesen möchten, kann [`read`](@ref) oder [`readchomp`](@ref) stattdessen verwendet werden:

```jldoctest
julia> read(`echo hello`, String)
"hello\n"

julia> readchomp(`echo hello`)
"hello"
```

Allgemeiner gesagt, können Sie [`open`](@ref) verwenden, um von einem externen Befehl zu lesen oder in ihn zu schreiben.

```jldoctest
julia> open(`less`, "w", stdout) do io
           for i = 1:3
               println(io, i)
           end
       end
1
2
3
```

Der Programmname und die einzelnen Argumente in einem Befehl können wie ein Array von Zeichenfolgen zugegriffen und durchlaufen werden:

```jldoctest
julia> collect(`echo "foo bar"`)
2-element Vector{String}:
 "echo"
 "foo bar"

julia> `echo "foo bar"`[2]
"foo bar"
```

## [Interpolation](@id command-interpolation)

Angenommen, Sie möchten etwas etwas Komplizierteres tun und den Namen einer Datei in der Variablen `file` als Argument für einen Befehl verwenden. Sie können `$` für die Interpolation verwenden, ähnlich wie Sie es in einem Stringliteral tun würden (siehe [Strings](@ref)):

```jldoctest
julia> file = "/etc/passwd"
"/etc/passwd"

julia> `sort $file`
`sort /etc/passwd`
```

Ein häufiges Problem beim Ausführen externer Programme über eine Shell ist, dass, wenn ein Dateiname Zeichen enthält, die für die Shell speziell sind, dies zu unerwünschtem Verhalten führen kann. Angenommen, wir möchten anstelle von `/etc/passwd` den Inhalt der Datei `/Volumes/External HD/data.csv` sortieren. Lassen Sie es uns versuchen:

```jldoctest
julia> file = "/Volumes/External HD/data.csv"
"/Volumes/External HD/data.csv"

julia> `sort $file`
`sort '/Volumes/External HD/data.csv'`
```

Wie wurde der Dateiname zitiert? Julia weiß, dass `file` als ein einzelnes Argument interpoliert werden soll, also zitiert sie das Wort für dich. Tatsächlich ist das nicht ganz genau: Der Wert von `file` wird niemals von einer Shell interpretiert, daher gibt es keinen Bedarf für tatsächliches Zitieren; die Anführungszeichen werden nur zur Präsentation für den Benutzer eingefügt. Das wird sogar funktionieren, wenn du einen Wert als Teil eines Shell-Wortes interpolierst:

```jldoctest
julia> path = "/Volumes/External HD"
"/Volumes/External HD"

julia> name = "data"
"data"

julia> ext = "csv"
"csv"

julia> `sort $path/$name.$ext`
`sort '/Volumes/External HD/data.csv'`
```

Wie Sie sehen können, ist der Abstand in der `path`-Variablen angemessen escaped. Aber was ist, wenn Sie *möchten*, dass mehrere Wörter interpoliert werden? In diesem Fall verwenden Sie einfach ein Array (oder einen anderen iterierbaren Container):

```jldoctest
julia> files = ["/etc/passwd","/Volumes/External HD/data.csv"]
2-element Vector{String}:
 "/etc/passwd"
 "/Volumes/External HD/data.csv"

julia> `grep foo $files`
`grep foo /etc/passwd '/Volumes/External HD/data.csv'`
```

Wenn Sie ein Array als Teil eines Shell-Worts interpolieren, emuliert Julia die Argumentgenerierung der Shell `{a,b,c}`:

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> `grep xylophone $names.txt`
`grep xylophone foo.txt bar.txt baz.txt`
```

Darüber hinaus, wenn Sie mehrere Arrays in dasselbe Wort interpolieren, wird das Verhalten der kartesischen Produktgenerierung der Shell emuliert:

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> exts = ["aux","log"]
2-element Vector{String}:
 "aux"
 "log"

julia> `rm -f $names.$exts`
`rm -f foo.aux foo.log bar.aux bar.log baz.aux baz.log`
```

Da Sie literale Arrays interpolieren können, können Sie diese generative Funktionalität nutzen, ohne zuerst temporäre Array-Objekte erstellen zu müssen:

```jldoctest
julia> `rm -rf $["foo","bar","baz","qux"].$["aux","log","pdf"]`
`rm -rf foo.aux foo.log foo.pdf bar.aux bar.log bar.pdf baz.aux baz.log baz.pdf qux.aux qux.log qux.pdf`
```

## Quoting

Inevitably, one wants to write commands that aren't quite so simple, and it becomes necessary to use quotes. Here's a simple example of a Perl one-liner at a shell prompt:

```
sh$ perl -le '$|=1; for (0..3) { print }'
0
1
2
3
```

Der Perl-Ausdruck muss aus zwei Gründen in einfache Anführungszeichen gesetzt werden: damit Leerzeichen den Ausdruck nicht in mehrere Shell-Wörter aufteilen und damit Verwendungen von Perl-Variablen wie `$|` (ja, das ist der Name einer Variablen in Perl) keine Interpolation verursachen. In anderen Fällen möchten Sie möglicherweise doppelte Anführungszeichen verwenden, damit die Interpolation *doch* erfolgt:

```
sh$ first="A"
sh$ second="B"
sh$ perl -le '$|=1; print for @ARGV' "1: $first" "2: $second"
1: A
2: B
```

Im Allgemeinen ist die Julia-Backtick-Syntax sorgfältig gestaltet, sodass Sie Shell-Befehle einfach so in Backticks einfügen können, und sie werden funktionieren: Die Escape-, Zitat- und Interpolationsverhalten sind die gleichen wie im Shell. Der einzige Unterschied besteht darin, dass die Interpolation integriert ist und sich der Vorstellung von Julia bewusst ist, was ein einzelner String-Wert ist und was ein Container für mehrere Werte ist. Lassen Sie uns die beiden obigen Beispiele in Julia ausprobieren:

```jldoctest
julia> A = `perl -le '$|=1; for (0..3) { print }'`
`perl -le '$|=1; for (0..3) { print }'`

julia> run(A);
0
1
2
3

julia> first = "A"; second = "B";

julia> B = `perl -le 'print for @ARGV' "1: $first" "2: $second"`
`perl -le 'print for @ARGV' '1: A' '2: B'`

julia> run(B);
1: A
2: B
```

Die Ergebnisse sind identisch, und Julias Interpolationsverhalten ahmt das der Shell nach, mit einigen Verbesserungen, da Julia erstklassige iterable Objekte unterstützt, während die meisten Shells Strings verwenden, die nach Leerzeichen aufgeteilt werden, was Mehrdeutigkeiten einführt. Wenn Sie versuchen, Shell-Befehle nach Julia zu portieren, versuchen Sie zuerst, sie zu kopieren und einzufügen. Da Julia Ihnen die Befehle vor der Ausführung anzeigt, können Sie deren Interpretation einfach und sicher überprüfen, ohne Schaden anzurichten.

## Pipelines

Shell-Metazeichen wie `|`, `&` und `>`, müssen innerhalb von Julias Backticks zitiert (oder escaped) werden:

```jldoctest
julia> run(`echo hello '|' sort`);
hello | sort

julia> run(`echo hello \| sort`);
hello | sort
```

Dieser Ausdruck ruft den `echo`-Befehl mit drei Wörtern als Argumenten auf: `hello`, `|` und `sort`. Das Ergebnis ist, dass eine einzelne Zeile ausgegeben wird: `hello | sort`. Wie konstruiert man dann eine Pipeline? Anstatt `'|'` innerhalb von Backticks zu verwenden, verwendet man [`pipeline`](@ref):

```jldoctest
julia> run(pipeline(`echo hello`, `sort`));
hello
```

Dies leitet die Ausgabe des `echo`-Befehls an den `sort`-Befehl weiter. Natürlich ist das nicht besonders interessant, da es nur eine Zeile zum Sortieren gibt, aber wir können sicherlich viel interessantere Dinge tun:

```julia-repl
julia> run(pipeline(`cut -d: -f3 /etc/passwd`, `sort -n`, `tail -n5`))
210
211
212
213
214
```

Dies gibt die höchsten fünf Benutzer-IDs auf einem UNIX-System aus. Die Befehle `cut`, `sort` und `tail` werden alle als unmittelbare Kinder des aktuellen `julia`-Prozesses gestartet, ohne dazwischenliegendem Shell-Prozess. Julia selbst erledigt die Arbeit, um Pipes einzurichten und Dateideskriptoren zu verbinden, die normalerweise von der Shell durchgeführt werden. Da Julia dies selbst macht, behält es eine bessere Kontrolle und kann einige Dinge tun, die Shells nicht können.

Julia kann mehrere Befehle parallel ausführen:

```jldoctest; filter = r"(world\nhello|hello\nworld)"
julia> run(`echo hello` & `echo world`);
world
hello
```

Die Reihenfolge der Ausgabe hier ist nicht deterministisch, da die beiden `echo`-Prozesse nahezu gleichzeitig gestartet werden und um den ersten Schreibzugriff auf den gemeinsamen [`stdout`](@ref)-Descriptor mit einander und dem `julia`-Elternprozess konkurrieren. Julia ermöglicht es Ihnen, die Ausgabe beider Prozesse an ein anderes Programm weiterzuleiten:

```jldoctest
julia> run(pipeline(`echo world` & `echo hello`, `sort`));
hello
world
```

In Bezug auf UNIX-Rohre geschieht hier Folgendes: Ein einzelnes UNIX-Pipe-Objekt wird erstellt und von beiden `echo`-Prozessen beschrieben, während das andere Ende des Rohrs vom `sort`-Befehl gelesen wird.

IO-Umleitung kann erreicht werden, indem die Schlüsselwortargumente `stdin`, `stdout` und `stderr` an die Funktion `pipeline` übergeben werden:

```julia
pipeline(`do_work`, stdout=pipeline(`sort`, "out.txt"), stderr="errs.txt")
```

### Avoiding Deadlock in Pipelines

Beim Lesen und Schreiben an beiden Enden einer Pipeline von einem einzelnen Prozess ist es wichtig, zu vermeiden, dass der Kernel gezwungen wird, alle Daten zwischenzuspeichern.

Zum Beispiel, wenn Sie die gesamte Ausgabe eines Befehls lesen, rufen Sie `read(out, String)` auf, nicht `wait(process)`, da ersteres aktiv alle von dem Prozess geschriebenen Daten konsumiert, während letzteres versucht, die Daten in den Puffern des Kernels zu speichern, während auf einen Leser gewartet wird, der verbunden wird.

Eine weitere gängige Lösung besteht darin, den Leser und den Schreiber der Pipeline in separate [`Task`](@ref) zu trennen:

```julia
writer = @async write(process, "data")
reader = @async do_compute(read(process, String))
wait(writer)
fetch(reader)
```

(gewöhnlich auch, ist der Leser keine separate Aufgabe, da wir ihn sowieso sofort `fetch`en).

### Complex Example

Die Kombination aus einer Hochsprache, einer erstklassigen Befehlsabstraktion und der automatischen Einrichtung von Pipes zwischen Prozessen ist eine mächtige. Um ein Gefühl für die komplexen Pipelines zu vermitteln, die leicht erstellt werden können, hier einige ausgefeiltere Beispiele, mit Entschuldigung für die übermäßige Verwendung von Perl-Einzeilern:

```jldoctest prefixer; filter = r"([A-B] [0-5])"
julia> prefixer(prefix, sleep) = `perl -nle '$|=1; print "'$prefix' ", $_; sleep '$sleep';'`;

julia> run(pipeline(`perl -le '$|=1; for(0..5){ print; sleep 1 }'`, prefixer("A",2) & prefixer("B",2)));
B 0
A 1
B 2
A 3
B 4
A 5
```

Dies ist ein klassisches Beispiel für einen einzelnen Produzenten, der zwei gleichzeitige Verbraucher speist: Ein `perl`-Prozess generiert Zeilen mit den Zahlen 0 bis 5, während zwei parallele Prozesse diese Ausgabe konsumieren, wobei der eine die Zeilen mit dem Buchstaben "A" und der andere mit dem Buchstaben "B" voranstellt. Welcher Verbraucher die erste Zeile erhält, ist nicht deterministisch, aber sobald dieses Rennen gewonnen ist, werden die Zeilen abwechselnd von einem Prozess und dann vom anderen konsumiert. (Das Setzen von `$|=1` in Perl bewirkt, dass jede Druckanweisung den [`stdout`](@ref)-Handle leert, was notwendig ist, damit dieses Beispiel funktioniert. Andernfalls wird die gesamte Ausgabe gepuffert und auf einmal an die Pipe ausgegeben, um von nur einem Verbraucherprozess gelesen zu werden.)

Hier ist ein noch komplexeres mehrstufiges Produzenten-Verbraucher-Beispiel:

```jldoctest prefixer; filter = r"[A-B] [X-Z] [0-5]"
julia> run(pipeline(`perl -le '$|=1; for(0..5){ print; sleep 1 }'`,
           prefixer("X",3) & prefixer("Y",3) & prefixer("Z",3),
           prefixer("A",2) & prefixer("B",2)));
A X 0
B Y 1
A Z 2
B X 3
A Y 4
B Z 5
```

Dieses Beispiel ist ähnlich wie das vorherige, mit dem Unterschied, dass es zwei Stufen von Verbrauchern gibt und die Stufen unterschiedliche Latenzen aufweisen, sodass sie eine unterschiedliche Anzahl von parallelen Arbeitern verwenden, um einen gesättigten Durchsatz aufrechtzuerhalten.

Wir empfehlen Ihnen dringend, all diese Beispiele auszuprobieren, um zu sehen, wie sie funktionieren.

## `Cmd` Objects

Die Backtick-Syntax erstellt ein Objekt vom Typ [`Cmd`](@ref). Ein solches Objekt kann auch direkt aus einem vorhandenen `Cmd` oder einer Liste von Argumenten erstellt werden:

```julia
run(Cmd(`pwd`, dir=".."))
run(Cmd(["pwd"], detach=true, ignorestatus=true))
```

Dies ermöglicht es Ihnen, mehrere Aspekte der Ausführungsumgebung des `Cmd` über Schlüsselwortargumente anzugeben. Zum Beispiel bietet das Schlüsselwort `dir` Kontrolle über das Arbeitsverzeichnis des `Cmd`:

```jldoctest
julia> run(Cmd(`pwd`, dir="/"));
/
```

Und das `env`-Schlüsselwort ermöglicht es Ihnen, Ausführungsumgebungsvariablen festzulegen:

```jldoctest
julia> run(Cmd(`sh -c "echo foo \$HOWLONG"`, env=("HOWLONG" => "ever!",)));
foo ever!
```

Siehe [`Cmd`](@ref) für zusätzliche Schlüsselwortargumente. Die Befehle [`setenv`](@ref) und [`addenv`](@ref) bieten eine weitere Möglichkeit, die Umgebungsvariablen der `Cmd`-Ausführung zu ersetzen oder hinzuzufügen.

```jldoctest
julia> run(setenv(`sh -c "echo foo \$HOWLONG"`, ("HOWLONG" => "ever!",)));
foo ever!

julia> run(addenv(`sh -c "echo foo \$HOWLONG"`, "HOWLONG" => "ever!"));
foo ever!
```
