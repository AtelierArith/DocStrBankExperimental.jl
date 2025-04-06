# Noteworthy Differences from other Languages

## Noteworthy differences from MATLAB

Obwohl MATLAB-Benutzer Julias Syntax möglicherweise vertraut finden, ist Julia kein MATLAB-Klon. Es gibt wesentliche syntaktische und funktionale Unterschiede. Die folgenden sind einige bemerkenswerte Unterschiede, die Julia-Benutzer, die an MATLAB gewöhnt sind, verwirren könnten:

  * Julia-Arrays werden mit eckigen Klammern indiziert, `A[i,j]`.
  * Julia-Arrays werden nicht kopiert, wenn sie einer anderen Variablen zugewiesen werden. Nach `A = B` wird eine Änderung der Elemente von `B` auch `A` ändern. Um dies zu vermeiden, verwenden Sie `A = copy(B)`.
  * Julia-Werte werden nicht kopiert, wenn sie an eine Funktion übergeben werden. Wenn eine Funktion ein Array ändert, sind die Änderungen im Aufrufer sichtbar.
  * Julia wächst Arrays in einer Zuweisungsanweisung nicht automatisch. Während in MATLAB `a(4) = 3.2` das Array `a = [0 0 0 3.2]` erstellen kann und `a(5) = 7` es auf `a = [0 0 0 3.2 7]` vergrößern kann, wirft die entsprechende Julia-Anweisung `a[5] = 7` einen Fehler, wenn die Länge von `a` kleiner als 5 ist oder wenn diese Anweisung die erste Verwendung des Identifikators `a` ist. Julia hat [`push!`](@ref) und [`append!`](@ref), die `Vector`s viel effizienter wachsen lassen als MATLABs `a(end+1) = val`.
  * Die imaginäre Einheit `sqrt(-1)` wird in Julia als [`im`](@ref) dargestellt, nicht als `i` oder `j` wie in MATLAB.
  * In Julia erzeugen Literalzahlen ohne Dezimalpunkt (wie `42`) Ganzzahlen anstelle von Fließkommazahlen. Infolgedessen können einige Operationen einen Bereichsfehler auslösen, wenn sie eine Fließkommazahl erwarten; zum Beispiel, `julia> a = -1; 2^a` löst einen Bereichsfehler aus, da das Ergebnis keine Ganzzahl ist (siehe [the FAQ entry on domain errors](@ref faq-domain-errors) für Details).
  * In Julia werden mehrere Werte als Tupel zurückgegeben und zugewiesen, z. B. `(a, b) = (1, 2)` oder `a, b = 1, 2`. MATLABs `nargout`, das häufig in MATLAB verwendet wird, um optionale Arbeiten basierend auf der Anzahl der zurückgegebenen Werte durchzuführen, existiert in Julia nicht. Stattdessen können Benutzer optionale und Schlüsselwortargumente verwenden, um ähnliche Funktionen zu erreichen.
  * Julia hat echte eindimensionale Arrays. Spaltenvektoren haben die Größe `N`, nicht `Nx1`. Zum Beispiel erzeugt [`rand(N)`](@ref) ein eindimensionales Array.
  * In Julia wird `[x,y,z]` immer ein 3-Elemente-Array erstellen, das `x`, `y` und `z` enthält.

      * Um in der ersten ("vertikalen") Dimension zu verketten, verwenden Sie entweder [`vcat(x,y,z)`](@ref) oder trennen Sie mit Semikolons (`[x; y; z]`).
      * Um in der zweiten ("horizontalen") Dimension zu verketten, verwenden Sie entweder [`hcat(x,y,z)`](@ref) oder trennen Sie mit Leerzeichen (`[x y z]`).
      * Um Blockmatrizen zu konstruieren (Konkatenation in den ersten beiden Dimensionen), verwenden Sie entweder [`hvcat`](@ref) oder kombinieren Sie Leerzeichen und Semikolons (`[a b; c d]`).
  * In Julia konstruiert `a:b` und `a:b:c` `AbstractRange`-Objekte. Um einen vollständigen Vektor wie in MATLAB zu erstellen, verwenden Sie [`collect(a:b)`](@ref). Im Allgemeinen ist es jedoch nicht notwendig, `collect` aufzurufen. Ein `AbstractRange`-Objekt verhält sich in den meisten Fällen wie ein normales Array, ist jedoch effizienter, da es seine Werte faul berechnet. Dieses Muster, spezialisierte Objekte anstelle vollständiger Arrays zu erstellen, wird häufig verwendet und ist auch in Funktionen wie [`range`](@ref) oder mit Iteratoren wie `enumerate` und `zip` zu sehen. Die speziellen Objekte können größtenteils so verwendet werden, als wären sie normale Arrays.
  * Funktionen in Julia geben Werte von ihrem letzten Ausdruck oder dem `return`-Schlüsselwort zurück, anstatt die Namen der Variablen in der Funktionsdefinition aufzulisten (siehe [The return Keyword](@ref) für Details).
  * Ein Julia-Skript kann beliebig viele Funktionen enthalten, und alle Definitionen sind sichtbar, wenn die Datei geladen wird. Funktionsdefinitionen können aus Dateien geladen werden, die sich außerhalb des aktuellen Arbeitsverzeichnisses befinden.
  * In Julia werden Reduktionen wie [`sum`](@ref), [`prod`](@ref) und [`maximum`](@ref) über jedes Element eines Arrays durchgeführt, wenn sie mit einem einzelnen Argument aufgerufen werden, wie in `sum(A)`, selbst wenn `A` mehr als eine Dimension hat.
  * In Julia müssen Klammern verwendet werden, um eine Funktion ohne Argumente aufzurufen, wie in [`rand()`](@ref).
  * Julia entmutigt die Verwendung von Semikolons zum Beenden von Anweisungen. Die Ergebnisse von Anweisungen werden nicht automatisch ausgegeben (außer an der interaktiven Eingabeaufforderung), und Codezeilen müssen nicht mit Semikolons enden. [`println`](@ref) oder [`@printf`](@ref) können verwendet werden, um spezifische Ausgaben zu drucken.
  * In Julia, wenn `A` und `B` Arrays sind, geben logische Vergleichsoperationen wie `A == B` kein Array von Booleans zurück. Verwenden Sie stattdessen `A .== B`, und ähnlich für die anderen booleschen Operatoren wie [`<`](@ref), [`>`](@ref).
  * In Julia führen die Operatoren [`&`](@ref), [`|`](@ref) und [`⊻`](@ref xor) ([`xor`](@ref)) die bitweisen Operationen aus, die in MATLAB `and`, `or` und `xor` entsprechen, und haben eine Präzedenz, die ähnlich ist wie die bitweisen Operatoren in Python (im Gegensatz zu C). Sie können auf Skalare oder elementweise über Arrays angewendet werden und können verwendet werden, um logische Arrays zu kombinieren, aber beachten Sie den Unterschied in der Reihenfolge der Operationen: Klammern können erforderlich sein (z. B. um Elemente von `A` auszuwählen, die gleich 1 oder 2 sind, verwenden Sie `(A .== 1) .| (A .== 2)`).
  * In Julia können die Elemente einer Sammlung als Argumente an eine Funktion über den Splat-Operator `...` übergeben werden, wie in `xs=[1,2]; f(xs...)`.
  * Julias [`svd`](@ref) gibt die singulären Werte als Vektor zurück, anstatt als dichte Diagonalmatrix.
  * In Julia wird `...` nicht verwendet, um Codezeilen fortzusetzen. Stattdessen setzen unvollständige Ausdrücke automatisch in die nächste Zeile fort.
  * In sowohl Julia als auch MATLAB wird die Variable `ans` auf den Wert des letzten in einer interaktiven Sitzung ausgegebenen Ausdrucks gesetzt. In Julia, im Gegensatz zu MATLAB, wird `ans` nicht gesetzt, wenn Julia-Code im nicht-interaktiven Modus ausgeführt wird.
  * Julias `struct`s unterstützen nicht das dynamische Hinzufügen von Feldern zur Laufzeit, im Gegensatz zu MATLABs `class`es. Stattdessen verwenden Sie ein [`Dict`](@ref). Dict in Julia ist nicht geordnet.
  * In Julia hat jedes Modul seinen eigenen globalen Geltungsbereich/Namensraum, während es in MATLAB nur einen globalen Geltungsbereich gibt.
  * In MATLAB ist eine idiomatische Möglichkeit, unerwünschte Werte zu entfernen, die Verwendung von logischer Indizierung, wie im Ausdruck `x(x>3)` oder in der Anweisung `x(x>3) = []`, um `x` vor Ort zu ändern. Im Gegensatz dazu bietet Julia die höherwertigen Funktionen [`filter`](@ref) und [`filter!`](@ref), die es den Benutzern ermöglichen, `filter(z->z>3, x)` und `filter!(z->z>3, x)` als Alternativen zu den entsprechenden Transliterationen `x[x.>3]` und `x = x[x.>3]` zu schreiben. Die Verwendung von `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` reduziert die Verwendung von temporären Arrays.
  * Die Analogie zum Extrahieren (oder "Dereferenzieren") aller Elemente eines Zellarrays, z. B. in `vertcat(A{:})` in MATLAB, wird in Julia mit dem Splat-Operator geschrieben, z. B. als `vcat(A...)`.
  * In Julia führt die Funktion `adjoint` die konjugierte Transposition durch; in MATLAB liefert `adjoint` die "Adjungierte" oder klassische Adjunkte, die die Transponierte der Matrix der Cofaktoren ist.
  * In Julia wird a^b^c als a^(b^c) ausgewertet, während es in MATLAB als (a^b)^c ausgewertet wird.

## Noteworthy differences from R

Eines von Julias Zielen ist es, eine effektive Sprache für Datenanalyse und statistisches Programmieren bereitzustellen. Für Benutzer, die von R zu Julia kommen, sind dies einige bemerkenswerte Unterschiede:

  * Julias einfache Anführungszeichen umschließen Zeichen, nicht Strings.
  * Julia kann Teilstrings erstellen, indem sie in Strings indiziert. In R müssen Strings in Zeichenvektoren umgewandelt werden, bevor Teilstrings erstellt werden.
  * In Julia, ähnlich wie in Python, aber im Gegensatz zu R, können Strings mit dreifachen Anführungszeichen `""" ... """` erstellt werden. Diese Syntax ist praktisch zum Erstellen von Strings, die Zeilenumbrüche enthalten.
  * In Julia werden varargs mit dem Splat-Operator `...` angegeben, der immer dem Namen einer bestimmten Variablen folgt, im Gegensatz zu R, wo `...` isoliert auftreten kann.
  * In Julia ist der Modulus `mod(a, b)`, nicht `a %% b`. `%` in Julia ist der Restoperator.
  * Julia konstruiert Vektoren mit Klammern. Julias `[1, 2, 3]` entspricht R's `c(1, 2, 3)`.
  * In Julia unterstützen nicht alle Datenstrukturen die logische Indizierung. Darüber hinaus wird die logische Indizierung in Julia nur mit Vektoren unterstützt, deren Länge gleich dem zu indizierenden Objekt ist. Zum Beispiel:

      * In R, `c(1, 2, 3, 4)[c(TRUE, FALSE)]` ist äquivalent zu `c(1, 3)`.
      * In R, `c(1, 2, 3, 4)[c(TRUE, FALSE, TRUE, FALSE)]` ist äquivalent zu `c(1, 3)`.
      * In Julia, `[1, 2, 3, 4][[true, false]]` wirft einen [`BoundsError`](@ref).
      * In Julia erzeugt `[1, 2, 3, 4][[true, false, true, false]]` `[1, 3]`.
  * Wie viele Sprachen erlaubt Julia nicht immer Operationen mit Vektoren unterschiedlicher Längen, im Gegensatz zu R, wo die Vektoren nur einen gemeinsamen Indexbereich teilen müssen. Zum Beispiel ist `c(1, 2, 3, 4) + c(1, 2)` gültiges R, aber das Äquivalent `[1, 2, 3, 4] + [1, 2]` wird in Julia einen Fehler auslösen.
  * Julia erlaubt ein optionales abschließendes Komma, wenn dieses Komma die Bedeutung des Codes nicht ändert. Dies kann bei R-Nutzern Verwirrung stiften, wenn sie in Arrays indizieren. Zum Beispiel würde `x[1,]` in R die erste Zeile einer Matrix zurückgeben; in Julia wird das Komma jedoch ignoriert, sodass `x[1,] == x[1]` gilt und das erste Element zurückgibt. Um eine Zeile zu extrahieren, verwenden Sie sicher `:`, wie in `x[1,:]`.
  * Julias [`map`](@ref) nimmt zuerst die Funktion und dann ihre Argumente, im Gegensatz zu `lapply(<structure>, function, ...)` in R. Ähnlich ist Julias Äquivalent von `apply(X, MARGIN, FUN, ...)` in R [`mapslices`](@ref), wo die Funktion das erste Argument ist.
  * Multivariate anwenden in R, z.B. `mapply(choose, 11:13, 1:3)`, kann in Julia als `broadcast(binomial, 11:13, 1:3)` geschrieben werden. Entsprechend bietet Julia eine kürzere Punkt-Syntax zur Vektorisierung von Funktionen `binomial.(11:13, 1:3)`.
  * Julia verwendet `end`, um das Ende von bedingten Blöcken wie `if`, Schleifenblöcken wie `while`/`for` und Funktionen zu kennzeichnen. Anstelle der einzeiligen `if ( cond ) statement` erlaubt Julia Anweisungen der Form `if cond; statement; end`, `cond && statement` und `!cond || statement`. Zuweisungsanweisungen in den letzten beiden Syntaxen müssen ausdrücklich in Klammern eingeschlossen werden, z. B. `cond && (x = value)`.
  * In Julia sind `<-`, `<<-` und `->` keine Zuweisungsoperatoren.
  * Julias `->` erstellt eine anonyme Funktion.
  * Julias [`*`](@ref) Operator kann Matrixmultiplikation durchführen, im Gegensatz zu R. Wenn `A` und `B` Matrizen sind, dann bezeichnet `A * B` eine Matrixmultiplikation in Julia, die R's `A %*% B` entspricht. In R würde dieselbe Notation eine elementweise (Hadamard) Multiplikation durchführen. Um die elementweise Multiplikation zu erhalten, müssen Sie in Julia `A .* B` schreiben.
  * Julia führt die Matrizen-Transposition mit der Funktion `transpose` durch und die konjugierte Transposition mit dem Operator `'` oder der Funktion `adjoint`. Julias `transpose(A)` entspricht daher R's `t(A)`. Darüber hinaus wird eine nicht-rekursive Transposition in Julia durch die Funktion `permutedims` bereitgestellt.
  * Julia benötigt keine Klammern, wenn sie `if`-Anweisungen oder `for`-/`while`-Schleifen schreibt: Verwenden Sie `for i in [1, 2, 3]` anstelle von `for (i in c(1, 2, 3))` und `if i == 1` anstelle von `if (i == 1)`.
  * Julia behandelt die Zahlen `0` und `1` nicht als Booleans. Sie können `if (1)` in Julia nicht schreiben, da `if`-Anweisungen nur Booleans akzeptieren. Stattdessen können Sie `if true`, `if Bool(1)` oder `if 1==1` schreiben.
  * Julia bietet `nrow` und `ncol` nicht an. Verwenden Sie stattdessen `size(M, 1)` für `nrow(M)` und `size(M, 2)` für `ncol(M)`.
  * Julia ist vorsichtig darin, Skalare, Vektoren und Matrizen zu unterscheiden. In R sind `1` und `c(1)` dasselbe. In Julia können sie nicht austauschbar verwendet werden.
  * Julias [`diag`](@ref) und [`diagm`](@ref) sind nicht wie R's.
  * Julia kann die Ergebnisse von Funktionsaufrufen auf der linken Seite einer Zuweisungsoperation nicht zuweisen: Sie können nicht `diag(M) = fill(1, n)` schreiben.
  * Julia rät davon ab, den Hauptnamensraum mit Funktionen zu füllen. Die meisten statistischen Funktionen für Julia finden sich in [packages](https://pkg.julialang.org/) unter [JuliaStats organization](https://github.com/JuliaStats). Zum Beispiel:

      * Funktionen, die sich auf Wahrscheinlichkeitsverteilungen beziehen, werden von der [Distributions package](https://github.com/JuliaStats/Distributions.jl) bereitgestellt.
      * Die [DataFrames package](https://github.com/JuliaData/DataFrames.jl) bietet Datenrahmen an.
      * Generalisierte lineare Modelle werden von der [GLM package](https://github.com/JuliaStats/GLM.jl) bereitgestellt.
  * Julia bietet Tupel und echte Hash-Tabellen, aber keine R-ähnlichen Listen. Wenn Sie mehrere Elemente zurückgeben, sollten Sie typischerweise ein Tupel oder ein benanntes Tupel verwenden: anstelle von `list(a = 1, b = 2)` verwenden Sie `(1, 2)` oder `(a=1, b=2)`.
  * Julia ermutigt Benutzer, ihre eigenen Typen zu schreiben, die einfacher zu verwenden sind als S3- oder S4-Objekte in R. Julias Mehrfachdispatch-System bedeutet, dass `table(x::TypeA)` und `table(x::TypeB)` wie R's `table.TypeA(x)` und `table.TypeB(x)` funktionieren.
  * In Julia werden Werte nicht kopiert, wenn sie zugewiesen oder an eine Funktion übergeben werden. Wenn eine Funktion ein Array ändert, sind die Änderungen im Aufrufer sichtbar. Dies ist sehr unterschiedlich zu R und ermöglicht es neuen Funktionen, viel effizienter mit großen Datenstrukturen zu arbeiten.
  * In Julia werden Vektoren und Matrizen mit [`hcat`](@ref), [`vcat`](@ref) und [`hvcat`](@ref) konkateniert, nicht mit `c`, `rbind` und `cbind` wie in R.
  * In Julia ist ein Bereich wie `a:b` kein Kurzschreibweise für einen Vektor wie in R, sondern ein spezialisiertes `AbstractRange`-Objekt, das für die Iteration verwendet wird. Um einen Bereich in einen Vektor umzuwandeln, verwenden Sie [`collect(a:b)`](@ref).
  * Der `:` Operator hat eine andere Priorität in R und Julia. Insbesondere haben in Julia arithmetische Operatoren eine höhere Priorität als der `:` Operator, während es in R umgekehrt ist. Zum Beispiel ist `1:n-1` in Julia äquivalent zu `1:(n-1)` in R.
  * Julias [`max`](@ref) und [`min`](@ref) sind das Äquivalent von `pmax` und `pmin` in R, aber beide Argumente müssen die gleichen Dimensionen haben. Während [`maximum`](@ref) und [`minimum`](@ref) `max` und `min` in R ersetzen, gibt es wichtige Unterschiede.
  * Julias [`sum`](@ref), [`prod`](@ref), [`maximum`](@ref) und [`minimum`](@ref) unterscheiden sich von ihren Gegenstücken in R. Sie akzeptieren alle ein optionales Schlüsselwortargument `dims`, das die Dimensionen angibt, über die die Operation durchgeführt wird. Zum Beispiel sei `A = [1 2; 3 4]` in Julia und `B <- rbind(c(1,2),c(3,4))` die gleiche Matrix in R. Dann ergibt `sum(A)` dasselbe Ergebnis wie `sum(B)`, aber `sum(A, dims=1)` ist ein Zeilenvektor, der die Summe über jede Spalte enthält, und `sum(A, dims=2)` ist ein Spaltenvektor, der die Summe über jede Zeile enthält. Dies steht im Gegensatz zum Verhalten von R, wo separate Funktionen `colSums(B)` und `rowSums(B)` diese Funktionalitäten bereitstellen. Wenn das Schlüsselwortargument `dims` ein Vektor ist, gibt es alle Dimensionen an, über die die Summe durchgeführt wird, während die Dimensionen des summierten Arrays beibehalten werden, z.B. `sum(A, dims=(1,2)) == hcat(10)`. Es sollte beachtet werden, dass es keine Fehlerüberprüfung bezüglich des zweiten Arguments gibt.
  * Julia hat mehrere Funktionen, die ihre Argumente verändern können. Zum Beispiel hat es sowohl [`sort`](@ref) als auch [`sort!`](@ref).
  * In R erfordert die Leistung Vektorisierung. In Julia ist fast das Gegenteil der Fall: Der am besten performende Code wird oft durch die Verwendung von devektorisierten Schleifen erreicht.
  * Julia wird eifrig ausgewertet und unterstützt keine R-ähnliche verzögerte Auswertung. Für die meisten Benutzer bedeutet dies, dass es sehr wenige unquoted Ausdrücke oder Spaltennamen gibt.
  * Julia unterstützt den `NULL`-Typ nicht. Das nächstgelegene Äquivalent ist [`nothing`](@ref), aber es verhält sich wie ein Skalarwert und nicht wie eine Liste. Verwenden Sie `x === nothing` anstelle von `is.null(x)`.
  * In Julia werden fehlende Werte durch das [`missing`](@ref) Objekt dargestellt, anstatt durch `NA`. Verwenden Sie [`ismissing(x)`](@ref) (oder `ismissing.(x)` für elementweise Operationen auf Vektoren) anstelle von `is.na(x)`. Die [`skipmissing`](@ref) Funktion wird im Allgemeinen anstelle von `na.rm=TRUE` verwendet (obwohl in einigen speziellen Fällen Funktionen ein `skipmissing` Argument akzeptieren).
  * Julia hat nicht das Äquivalent von R's `assign` oder `get`.
  * In Julia erfordert `return` keine Klammern.
  * In R ist eine idiomatische Möglichkeit, unerwünschte Werte zu entfernen, die Verwendung von logischer Indizierung, wie im Ausdruck `x[x>3]` oder in der Anweisung `x = x[x>3]`, um `x` vor Ort zu ändern. Im Gegensatz dazu bietet Julia die höherwertigen Funktionen [`filter`](@ref) und [`filter!`](@ref), die es den Benutzern ermöglichen, `filter(z->z>3, x)` und `filter!(z->z>3, x)` als Alternativen zu den entsprechenden Transliterationen `x[x.>3]` und `x = x[x.>3]` zu schreiben. Die Verwendung von `4d61726b646f776e2e436f64652822222c202266696c746572212229_40726566` reduziert die Verwendung von temporären Arrays.

## Noteworthy differences from Python

  * Julias `for`, `if`, `while` usw. Blöcke werden durch das Schlüsselwort `end` beendet. Die Einrückungsebene ist nicht so bedeutend wie in Python. Im Gegensatz zu Python hat Julia kein `pass`-Schlüsselwort.
  * Strings werden in Julia durch doppelte Anführungszeichen (`"text"`) dargestellt (mit drei doppelten Anführungszeichen für mehrzeilige Strings), während sie in Python entweder durch einfache (`'text'`) oder doppelte Anführungszeichen (`"text"`) dargestellt werden können. Einfache Anführungszeichen werden in Julia für Zeichen verwendet (`'c'`).
  * Stringverkettung wird in Julia mit `*` durchgeführt, nicht mit `+` wie in Python. Analog dazu wird die Stringwiederholung mit `^` durchgeführt, nicht mit `*`. Implizite Stringverkettung von Stringliteralen wie in Python (z.B. `'ab' 'cd' == 'abcd'`) wird in Julia nicht durchgeführt.
  * Python-Listen – flexibel, aber langsam – entsprechen dem Julia-Typ `Vector{Any}` oder allgemeiner `Vector{T}`, wobei `T` ein nicht-konkreter Elementtyp ist. "Schnelle" Arrays wie NumPy-Arrays, die Elemente vor Ort speichern (d.h. `dtype` ist `np.float64`, `[('f1', np.uint64), ('f2', np.int32)]` usw.), können durch `Array{T}` dargestellt werden, wobei `T` ein konkreter, unveränderlicher Elementtyp ist. Dazu gehören eingebaute Typen wie `Float64`, `Int32`, `Int64`, aber auch komplexere Typen wie `Tuple{UInt64,Float64}` und viele benutzerdefinierte Typen.
  * In Julia beginnt die Indizierung von Arrays, Strings usw. bei 1 und nicht bei 0.
  * Julias Slice-Indexierung umfasst das letzte Element, im Gegensatz zu Python. `a[2:3]` in Julia entspricht `a[1:3]` in Python.
  * Im Gegensatz zu Python erlaubt Julia [AbstractArrays with arbitrary indexes](https://julialang.org/blog/2017/04/offset-arrays/). Pythons spezielle Interpretation von negativem Indexing, `a[-1]` und `a[-2]`, sollte in Julia als `a[end]` und `a[end-1]` geschrieben werden.
  * Julia benötigt `end` für die Indizierung bis zum letzten Element. `x[1:]` in Python entspricht `x[2:end]` in Julia.
  * In Julia erstellt `:` vor einem Objekt einen [`Symbol`](@ref) oder *zitiert* einen Ausdruck; daher ist `x[:5]` dasselbe wie `x[5]`. Wenn Sie die ersten `n` Elemente eines Arrays erhalten möchten, verwenden Sie die Bereichsindizierung.
  * Julias Bereichsindizierung hat das Format `x[start:step:stop]`, während das Format von Python `x[start:(stop+1):step]` ist. Daher entspricht `x[0:10:2]` in Python `x[1:2:10]` in Julia. Ebenso entspricht `x[::-1]` in Python, das auf das umgekehrte Array verweist, `x[end:-1:1]` in Julia.
  * In Julia können Bereiche unabhängig als `start:step:stop` konstruiert werden, dieselbe Syntax, die auch beim Array-Indexing verwendet wird. Die `range`-Funktion wird ebenfalls unterstützt.
  * In Julia bezieht sich das Indizieren einer Matrix mit Arrays wie `X[[1,2], [1,3]]` auf eine Untermatrix, die die Schnittpunkte der ersten und zweiten Zeilen mit der ersten und dritten Spalte enthält. In Python bezieht sich `X[[1,2], [1,3]]` auf einen Vektor, der die Werte der Zellen `[1,1]` und `[2,3]` in der Matrix enthält. `X[[1,2], [1,3]]` in Julia entspricht `X[np.ix_([0,1],[0,2])]` in Python. `X[[0,1], [0,2]]` in Python entspricht `X[[CartesianIndex(1,1), CartesianIndex(2,3)]]` in Julia.
  * Julia hat keine Zeilenfortsetzungs-Syntax: Wenn am Ende einer Zeile der bisherige Eingabe ein vollständiger Ausdruck ist, wird er als abgeschlossen betrachtet; andernfalls wird die Eingabe fortgesetzt. Eine Möglichkeit, einen Ausdruck zur Fortsetzung zu zwingen, besteht darin, ihn in Klammern zu setzen.
  * Julia-Arrays sind spaltenmajor (Fortran-geordnet), während NumPy-Arrays standardmäßig zeilenmajor (C-geordnet) sind. Um eine optimale Leistung beim Durchlaufen von Arrays zu erzielen, sollte die Reihenfolge der Schleifen in Julia im Vergleich zu NumPy umgekehrt werden (siehe [relevant section of Performance Tips](@ref man-performance-column-major)).
  * Julias Aktualisierungsoperatoren (z. B. `+=`, `-=`, ...) sind *nicht in-place*, während die von NumPy es sind. Das bedeutet, dass `A = [1, 1]; B = A; B += [3, 3]` die Werte in `A` nicht ändert, sondern den Namen `B` an das Ergebnis der rechten Seite `B = B + 3` neu bindet, was ein neues Array ist. Für in-place Operationen verwenden Sie `B .+= 3` (siehe auch [dot operators](@ref man-dot-operators)), explizite Schleifen oder `InplaceOps.jl`.
  * Julia bewertet Standardwerte von Funktionsargumenten jedes Mal, wenn die Methode aufgerufen wird, im Gegensatz zu Python, wo die Standardwerte nur einmal ausgewertet werden, wenn die Funktion definiert wird. Zum Beispiel gibt die Funktion `f(x=rand()) = x` jedes Mal eine neue Zufallszahl zurück, wenn sie ohne Argument aufgerufen wird. Andererseits gibt die Funktion `g(x=[1,2]) = push!(x,3)` jedes Mal `[1,2,3]` zurück, wenn sie als `g()` aufgerufen wird.
  * In Julia müssen Schlüsselwortargumente mit Schlüsselwörtern übergeben werden, im Gegensatz zu Python, wo es normalerweise möglich ist, sie positionsbasiert zu übergeben. Der Versuch, ein Schlüsselwortargument positionsbasiert zu übergeben, ändert die Methodensignatur, was zu einem `MethodError` oder dem Aufruf der falschen Methode führt.
  * In Julia `%` ist der Restoperator, während es in Python der Modulus ist.
  * In Julia entspricht der häufig verwendete `Int`-Typ dem Maschineninteger-Typ (`Int32` oder `Int64`), im Gegensatz zu Python, wo `int` ein ganzzahliger Typ beliebiger Länge ist. Das bedeutet, dass der `Int`-Typ in Julia überlaufen kann, sodass `2^64 == 0` ergibt. Wenn Sie größere Werte benötigen, verwenden Sie einen anderen geeigneten Typ, wie `Int128`, [`BigInt`](@ref) oder einen Fließkommatyp wie `Float64`.
  * Die imaginäre Einheit `sqrt(-1)` wird in Julia als `im` dargestellt, nicht als `j` wie in Python.
  * In Julia ist der Exponentenoperator `^`, nicht `**` wie in Python.
  * Julia verwendet `nothing` vom Typ `Nothing`, um einen Nullwert darzustellen, während Python `None` vom Typ `NoneType` verwendet.
  * In Julia sind die Standardoperatoren über einen Matrizen-Typ Matrixoperationen, während in Python die Standardoperatoren elementweise Operationen sind. Wenn sowohl `A` als auch `B` Matrizen sind, führt `A * B` in Julia eine Matrixmultiplikation durch, nicht eine elementweise Multiplikation wie in Python. `A * B` in Julia entspricht `A @ B` in Python, während `A * B` in Python `A .* B` in Julia entspricht.
  * Der adjungierte Operator `'` in Julia gibt einen Adjunkten eines Vektors zurück (eine faule Darstellung eines Zeilenvektors), während der Transpose-Operator `.T` über einen Vektor in Python den ursprünglichen Vektor zurückgibt (keine Operation).
  * In Julia kann eine Funktion mehrere konkrete Implementierungen (genannt *Methoden*) enthalten, die über Mehrfachdispatch basierend auf den Typen aller Argumente des Aufrufs ausgewählt werden, im Vergleich zu Funktionen in Python, die eine einzige Implementierung und keine Polymorphie haben (im Gegensatz zu Python-Methodeaufrufen, die eine andere Syntax verwenden und das Dispatching auf den Empfänger der Methode ermöglichen).
  * Es gibt keine Klassen in Julia. Stattdessen gibt es Strukturen (veränderlich oder unveränderlich), die Daten enthalten, aber keine Methoden.
  * Das Aufrufen einer Methode einer Klasseninstanz in Python (`x = MyClass(*args); x.f(y)`) entspricht einem Funktionsaufruf in Julia, z.B. `x = MyType(args...); f(x, y)`. Im Allgemeinen ist das multiple Dispatch flexibler und leistungsfähiger als das Python-Klassensystem.
  * Julia-Strukturen können genau einen abstrakten Supertyp haben, während Python-Klassen von einem oder mehreren (abstrakten oder konkreten) Superklassen erben können.
  * Die logische Julia-Programmierstruktur (Pakete und Module) ist unabhängig von der Dateistruktur, während die Python-Code-Struktur durch Verzeichnisse (Pakete) und Dateien (Module) definiert ist.
  * In Julia ist es idiomatisch, den Text großer Module in mehrere Dateien aufzuteilen, ohne pro Datei ein neues Modul einzuführen. Der Code wird in einer Hauptdatei innerhalb eines einzelnen Moduls über `include` wieder zusammengesetzt. Während das Python-Äquivalent (`exec`) für diesen Zweck nicht typisch ist (es wird vorherige Definitionen stillschweigend überschreiben), werden Julia-Programme als Einheit auf Modulebene mit `using` oder `import` definiert, die nur einmal ausgeführt werden, wenn sie zum ersten Mal benötigt werden – ähnlich wie `include` in Python. Innerhalb dieser Module werden die einzelnen Dateien, die dieses Modul ausmachen, mit `include` geladen, indem sie einmal in der beabsichtigten Reihenfolge aufgelistet werden.
  * Der ternäre Operator `x > 0 ? 1 : -1` in Julia entspricht einem bedingten Ausdruck in Python `1 if x > 0 else -1`.
  * In Julia bezieht sich das `@`-Symbol auf ein Makro, während es in Python auf einen Dekorator verweist.
  * Die Ausnahmebehandlung in Julia erfolgt mit `try` — `catch` — `finally`, anstelle von `try` — `except` — `finally`. Im Gegensatz zu Python wird nicht empfohlen, die Ausnahmebehandlung als Teil des normalen Arbeitsablaufs in Julia zu verwenden (im Vergleich zu Python ist Julia bei gewöhnlichem Kontrollfluss schneller, aber langsamer bei der Ausnahmebehandlung).
  * In Julia sind Schleifen schnell, es ist nicht notwendig, aus Leistungsgründen "vektorisierten" Code zu schreiben.
  * Sei vorsichtig mit nicht-konstanten globalen Variablen in Julia, insbesondere in engen Schleifen. Da du in Julia (im Gegensatz zu Python) nahezu hardwarenahe Code schreiben kannst, kann die Auswirkung von globalen Variablen drastisch sein (siehe [Performance Tips](@ref man-performance-tips)).
  * In Julia sind Rundung und Trunkierung explizit. Pythons `int(3.7)` sollte `floor(Int, 3.7)` oder `Int(floor(3.7))` sein und unterscheidet sich von `round(Int, 3.7)`. `floor(x)` und `round(x)` geben für sich genommen einen ganzzahligen Wert des gleichen Typs wie `x` zurück, anstatt immer `Int` zurückzugeben.
  * In Julia ist das Parsen explizit. Pythons `float("3.7")` wäre `parse(Float64, "3.7")` in Julia.
  * In Python können die meisten Werte in logischen Kontexten verwendet werden (z. B. bedeutet `if "a":`, dass der folgende Block ausgeführt wird, und `if "":`, dass dies nicht der Fall ist). In Julia müssen Sie eine explizite Umwandlung in `Bool` vornehmen (z. B. wirft `if "a"` eine Ausnahme). Wenn Sie in Julia auf einen nicht leeren String testen möchten, würden Sie explizit `if !isempty("")` schreiben. Vielleicht überraschend ist, dass in Python `if "False"` und `bool("False")` beide zu `True` ausgewertet werden (weil `"False"` ein nicht leerer String ist); in Julia gibt `parse(Bool, "false")` `false` zurück.
  * In Julia wird ein neuer lokaler Geltungsbereich durch die meisten Codeblöcke eingeführt, einschließlich Schleifen und `try` — `catch` — `finally`. Beachten Sie, dass Komprehensionen (Listen, Generatoren usw.) sowohl in Python als auch in Julia einen neuen lokalen Geltungsbereich einführen, während `if`-Blöcke in beiden Sprachen keinen neuen lokalen Geltungsbereich einführen.

## Noteworthy differences from C/C++

  * Julia-Arrays werden mit eckigen Klammern indiziert und können mehr als eine Dimension haben `A[i,j]`. Diese Syntax ist nicht nur syntaktischer Zucker für einen Verweis auf einen Zeiger oder eine Adresse wie in C/C++. Siehe [the manual entry about array construction](@ref man-multi-dim-arrays).
  * In Julia beginnt die Indizierung von Arrays, Strings usw. bei 1 und nicht bei 0.
  * Julia-Arrays werden nicht kopiert, wenn sie einer anderen Variablen zugewiesen werden. Nach `A = B` wird das Ändern von Elementen in `B` auch `A` ändern. Aktualisierungsoperatoren wie `+=` arbeiten nicht in-place, sie sind äquivalent zu `A = A + B`, was die linke Seite an das Ergebnis des Ausdrucks auf der rechten Seite bindet.
  * Julia-Arrays sind spaltenmajor (Fortran-geordnet), während C/C++-Arrays standardmäßig zeilenmajor geordnet sind. Um eine optimale Leistung beim Durchlaufen von Arrays zu erzielen, sollte die Reihenfolge der Schleifen in Julia im Vergleich zu C/C++ umgekehrt werden (siehe [relevant section of Performance Tips](@ref man-performance-column-major)).
  * Julia-Werte werden nicht kopiert, wenn sie zugewiesen oder an eine Funktion übergeben werden. Wenn eine Funktion ein Array ändert, sind die Änderungen im Aufrufer sichtbar.
  * In Julia ist Leerraum signifikant, im Gegensatz zu C/C++, daher muss beim Hinzufügen/Entfernen von Leerraum in einem Julia-Programm Vorsicht walten.
  * In Julia erzeugen Literalzahlen ohne Dezimalpunkt (wie `42`) vorzeichenbehaftete Ganzzahlen vom Typ `Int`, aber Literale, die zu groß sind, um in die Maschinenwortgröße zu passen, werden automatisch auf einen größeren Typ, wie `Int64` (wenn `Int` `Int32` ist), `Int128` oder den beliebig großen Typ `BigInt` hochgestuft. Es gibt keine numerischen Literal-Suffixe wie `L`, `LL`, `U`, `UL`, `ULL`, um vorzeichenbehaftet und/oder vorzeichenlos anzuzeigen. Dezimalliterale sind immer vorzeichenbehaftet, und hexadezimale Literale (die mit `0x` beginnen, wie in C/C++), sind vorzeichenlos, es sei denn, sie kodieren mehr als 128 Bits, in diesem Fall sind sie vom Typ `BigInt`. Hexadezimale Literale haben auch, im Gegensatz zu C/C++/Java und im Gegensatz zu Dezimalliteralen in Julia, einen Typ, der auf der *Länge* des Literals basiert, einschließlich führender Nullen. Zum Beispiel haben `0x0` und `0x00` den Typ [`UInt8`](@ref), `0x000` und `0x0000` haben den Typ [`UInt16`](@ref), dann haben Literale mit 5 bis 8 Hex-Ziffern den Typ `UInt32`, 9 bis 16 Hex-Ziffern den Typ `UInt64`, 17 bis 32 Hex-Ziffern den Typ `UInt128`, und mehr als 32 Hex-Ziffern den Typ `BigInt`. Dies muss bei der Definition von hexadezimalen Masken berücksichtigt werden, zum Beispiel ist `~0xf == 0xf0` sehr unterschiedlich von `~0x000f == 0xfff0`. 64-Bit `Float64` und 32-Bit [`Float32`](@ref) Bit-Literale werden als `1.0` und `1.0f0` ausgedrückt. Gleitkommaliterale werden gerundet (und nicht auf den Typ `BigFloat` hochgestuft), wenn sie nicht genau dargestellt werden können. Gleitkommaliterale verhalten sich näher an C/C++. Oktal (mit `0o` vorangestellt) und binäre (mit `0b` vorangestellt) Literale werden ebenfalls als vorzeichenlos behandelt (oder `BigInt` für mehr als 128 Bits).
  * In Julia gibt der Divisionsoperator [`/`](@ref) eine Fließkommazahl zurück, wenn beide Operanden vom Ganzzahltyp sind. Um eine Ganzzahldivision durchzuführen, verwenden Sie [`div`](@ref) oder [`÷`](@ref div).
  * Das Indizieren eines `Array` mit Gleitkommatypen ist in der Regel ein Fehler in Julia. Der Julia-Äquivalent des C-Ausdrucks `a[i / 2]` ist `a[i ÷ 2 + 1]`, wobei `i` vom Ganzzahltyp ist.
  * String-Literale können entweder mit `"` oder `"""` begrenzt werden. Mit `"""` begrenzte Literale können `"`-Zeichen enthalten, ohne sie zu zitieren, wie `"\""`. String-Literale können Werte anderer Variablen oder Ausdrücke enthalten, die in sie interpoliert werden, angezeigt durch `$variablename` oder `$(expression)`, was den Variablennamen oder den Ausdruck im Kontext der Funktion auswertet.
  * `//` zeigt eine [`Rational`](@ref) Zahl an und ist kein einzeiliger Kommentar (der in Julia `#` ist)
  * `#=` zeigt den Beginn eines mehrzeiligen Kommentars an, und `=#` beendet ihn.
  * Funktionen in Julia geben Werte von ihrem letzten Ausdruck oder dem `return`-Schlüsselwort zurück. Mehrere Werte können aus Funktionen zurückgegeben und als Tupel zugewiesen werden, z.B. `(a, b) = myfunction()` oder `a, b = myfunction()`, anstatt wie in C/C++ Zeiger auf Werte übergeben zu müssen (d.h. `a = myfunction(&b)`).
  * Julia benötigt keine Semikolons, um Anweisungen zu beenden. Die Ergebnisse von Ausdrücken werden nicht automatisch ausgegeben (außer an der interaktiven Eingabeaufforderung, d.h. dem REPL), und Codezeilen müssen nicht mit Semikolons enden. [`println`](@ref) oder [`@printf`](@ref) können verwendet werden, um spezifische Ausgaben zu drucken. Im REPL kann `;` verwendet werden, um die Ausgabe zu unterdrücken. `;` hat auch eine andere Bedeutung innerhalb von `[ ]`, was man beachten sollte. `;` kann verwendet werden, um Ausdrücke in einer einzigen Zeile zu trennen, ist jedoch in vielen Fällen nicht unbedingt erforderlich und dient eher der Lesbarkeit.
  * In Julia führt der Operator [`⊻`](@ref xor) ([`xor`](@ref)) die bitweise XOR-Operation durch, d.h. [`^`](@ref) in C/C++. Außerdem haben die bitweisen Operatoren nicht die gleiche Priorität wie in C/C++, daher können Klammern erforderlich sein.
  * Julias [`^`](@ref) ist Exponentiation (pow), nicht bitweises XOR wie in C/C++ (verwende [`⊻`](@ref xor) oder [`xor`](@ref) in Julia)
  * Julia hat zwei Rechtsverschiebungsoperatoren, `>>` und `>>>`. `>>` führt eine arithmetische Verschiebung durch, `>>>` führt immer eine logische Verschiebung durch, im Gegensatz zu C/C++, wo die Bedeutung von `>>` von dem Typ des verschobenen Wertes abhängt.
  * Julias `->` erstellt eine anonyme Funktion, es greift nicht über einen Zeiger auf ein Mitglied zu.
  * Julia benötigt keine Klammern, wenn sie `if`-Anweisungen oder `for`-/`while`-Schleifen schreibt: Verwenden Sie `for i in [1, 2, 3]` anstelle von `for (int i=1; i <= 3; i++)` und `if i == 1` anstelle von `if (i == 1)`.
  * Julia behandelt die Zahlen `0` und `1` nicht als Booleans. Sie können `if (1)` in Julia nicht schreiben, da `if`-Anweisungen nur Booleans akzeptieren. Stattdessen können Sie `if true`, `if Bool(1)` oder `if 1==1` schreiben.
  * Julia verwendet `end`, um das Ende von bedingten Blöcken wie `if`, Schleifenblöcken wie `while`/`for` und Funktionen zu kennzeichnen. Anstelle der einzeiligen `if ( cond ) statement` erlaubt Julia Anweisungen der Form `if cond; statement; end`, `cond && statement` und `!cond || statement`. Zuweisungsanweisungen in den letzten beiden Syntaxen müssen ausdrücklich in Klammern gesetzt werden, z. B. `cond && (x = value)`, aufgrund der Operatorpriorität.
  * Julia hat keine Zeilenfortsetzungs-Syntax: Wenn am Ende einer Zeile der bisherige Eingabe ein vollständiger Ausdruck ist, wird er als abgeschlossen betrachtet; andernfalls wird die Eingabe fortgesetzt. Eine Möglichkeit, einen Ausdruck zur Fortsetzung zu zwingen, besteht darin, ihn in Klammern zu setzen.
  * Julia-Makros arbeiten mit geparsten Ausdrücken und nicht mit dem Text des Programms, was ihnen ermöglicht, komplexe Transformationen von Julia-Code durchzuführen. Makronamen beginnen mit dem `@`-Zeichen und haben sowohl eine funktionsähnliche Syntax, `@mymacro(arg1, arg2, arg3)`, als auch eine statementsähnliche Syntax, `@mymacro arg1 arg2 arg3`. Die Formen sind austauschbar; die funktionsähnliche Form ist besonders nützlich, wenn das Makro innerhalb eines anderen Ausdrucks erscheint, und ist oft am klarsten. Die statementsähnliche Form wird häufig verwendet, um Blöcke zu annotieren, wie im verteilten `for`-Konstrukt: `@distributed for i in 1:n; #= body =#; end`. Wenn das Ende des Makrokonstrukts unklar sein könnte, verwenden Sie die funktionsähnliche Form.
  * Julia hat einen Aufzählungstyp, der mit dem Makro `@enum(name, value1, value2, ...)` ausgedrückt wird. Zum Beispiel: `@enum(Fruit, banana=1, apple, pear)`
  * Nach der Konvention haben Funktionen, die ihre Argumente ändern, ein `!` am Ende des Namens, zum Beispiel `push!`.
  * In C++ haben Sie standardmäßig eine statische Dispatch, d.h. Sie müssen eine Funktion als virtuell kennzeichnen, um einen dynamischen Dispatch zu haben. Auf der anderen Seite ist in Julia jede Methode "virtuell" (obwohl es allgemeiner ist, da Methoden auf jeden Argumenttyp dispatcht werden, nicht nur auf `this`, unter Verwendung der Regel der spezifischsten Deklaration).

### Julia ⇔ C/C++: Namespaces

  * C/C++ `namespace`s entsprechen ungefähr Julia `module`s.
  * Es gibt keine privaten globalen Variablen oder Felder in Julia. Alles ist über vollständig qualifizierte Pfade (oder relative Pfade, wenn gewünscht) öffentlich zugänglich.
  * `using MyNamespace::myfun` (C++) entspricht ungefähr `import MyModule: myfun` (Julia).
  * `using namespace MyNamespace` (C++) entspricht ungefähr `using MyModule` (Julia)

      * In Julia sind nur `export`ierte Symbole im aufrufenden Modul verfügbar.
      * In C++ sind nur die in den inkludierten (öffentlichen) Header-Dateien gefundenen Elemente verfügbar.
  * Hinweis: Die Schlüsselwörter `import`/`using` (Julia) *laden* ebenfalls Module (siehe unten).
  * Hinweis: `import`/`using` (Julia) funktioniert nur auf der Ebene des globalen Geltungsbereichs (`module`s)

      * In C++ funktioniert `using namespace X` innerhalb beliebiger Bereiche (z. B. Funktionsbereich).

### Julia ⇔ C/C++: Module loading

  * Wenn Sie an eine C/C++ "**Bibliothek**" denken, suchen Sie wahrscheinlich nach einem Julia "**Paket**".

      * Hinweis: C/C++-Bibliotheken beherbergen oft mehrere "Softwaremodule", während Julia "Pakete" typischerweise eines beherbergen.
      * Erinnerung: Julia `module`s sind globale Scopes (nicht unbedingt "Softwaremodule").
  * **Anstelle von build/`make`-Skripten** verwendet Julia "Projektumgebungen" (manchmal auch "Projekt" oder "Umgebung" genannt).

      * Build-Skripte sind nur für komplexere Anwendungen erforderlich (wie solche, die das Kompilieren oder Herunterladen von C/C++-Ausführungsdateien benötigen).
      * Um eine Anwendung oder ein Projekt in Julia zu entwickeln, können Sie das Stammverzeichnis als "Projektumgebung" initialisieren und dort anwendungsspezifischen Code/Pakete unterbringen. Dies bietet eine gute Kontrolle über die Projektabhängigkeiten und zukünftige Reproduzierbarkeit.
      * Verfügbare Pakete werden mit der Funktion `Pkg.add()` oder im Pkg REPL-Modus zu einer "Projektumgebung" hinzugefügt. (Dies **lädt** das genannte Paket jedoch nicht).
      * Die Liste der verfügbaren Pakete (direkte Abhängigkeiten) für eine "Projektumgebung" wird in der Datei `Project.toml` gespeichert.
      * Die *vollständigen* Abhängigkeitsinformationen für eine "Projektumgebung" werden automatisch generiert und in der Datei `Manifest.toml` von `Pkg.resolve()` gespeichert.
  * Pakete ("Softwaremodule"), die im "Projektumfeld" verfügbar sind, werden mit `import` oder `using` geladen.

      * In C/C++ fügst du `#include <moduleheader>` ein, um Objekt-/Funktionsdeklarationen zu erhalten, und verlinkst in Bibliotheken, wenn du die ausführbare Datei erstellst.
      * In Julia bringt das erneute Aufrufen von using/import das vorhandene Modul nur in den Geltungsbereich, lädt es jedoch nicht erneut (ähnlich wie das Hinzufügen des nicht standardmäßigen `#pragma once` in C/C++).
  * **Verzeichnisbasierte Paket-Repositories** (Julia) können verfügbar gemacht werden, indem Repository-Pfade zum `Base.LOAD_PATH`-Array hinzugefügt werden.

      * Pakete aus verzeichnisbasierten Repositories erfordern nicht das Tool `Pkg.add()`, bevor sie mit `import` oder `using` geladen werden. Sie sind einfach für das Projekt verfügbar.
      * Verzeichnisbasierte Paket-Repositorys sind die **schnellste Lösung**, um lokale Bibliotheken von "Softwaremodulen" zu entwickeln.

### Julia ⇔ C/C++: Assembling modules

  * In C/C++, `.c`/`.cpp`-Dateien werden kompiliert und mit Build-/`make`-Skripten zu einer Bibliothek hinzugefügt.

      * In Julia laden `import [PkgName]`/`using [PkgName]` Anweisungen `[PkgName].jl`, die sich im Unterverzeichnis `[PkgName]/src/` eines Pakets befinden.
      * In der Regel lädt `[PkgName].jl` zugehörige Quelldateien mit Aufrufen von `include "[someotherfile].jl"`.
  * `include "./path/to/somefile.jl"` (Julia) ist sehr ähnlich zu `#include "./path/to/somefile.jl"` (C/C++).

      * Allerdings wird `include "..."` (Julia) nicht verwendet, um Header-Dateien einzufügen (nicht erforderlich).
      * **Verwenden Sie nicht** `include "..."` (Julia), um Code aus anderen "Softwaremodulen" zu laden (verwenden Sie stattdessen `import`/`using`).
      * `include "path/to/some/module.jl"` (Julia) würde mehrere Versionen desselben Codes in verschiedenen Modulen instanziieren (distincte Typen (usw.) mit denselben Namen erstellen).
      * `include "somefile.jl"` wird typischerweise verwendet, um mehrere Dateien *innerhalb desselben Julia-Pakets* ("Softwaremodul") zusammenzustellen. Es ist daher relativ einfach sicherzustellen, dass Dateien nur einmal `include`d werden (keine `#ifdef`-Verwirrung).

### Julia ⇔ C/C++: Module interface

  * C++ stellt Schnittstellen über "öffentliche" `.h`/`.hpp`-Dateien zur Verfügung, während Julia `module`s bestimmte Symbole, die für ihre Benutzer bestimmt sind, als `public` oder `export` markiert.

      * Oftentimes fügen Julia `module`s einfach Funktionalität hinzu, indem sie neue "Methoden" zu bestehenden Funktionen generieren (z.B. `Base.push!`).
      * Entwickler von Julia-Paketen können daher nicht auf Header-Dateien für die Schnittstellendokumentation vertrauen.
      * Schnittstellen für Julia-Pakete werden typischerweise mit Docstrings, README.md, statischen Webseiten usw. beschrieben.
  * Einige Entwickler entscheiden sich dafür, nicht alle Symbole, die zum Verwenden ihres Pakets/Moduls erforderlich sind, zu `exportieren`, sollten jedoch nicht exportierte, benutzerorientierte Symbole als `öffentlich` kennzeichnen.

      * Benutzer könnten erwarten, auf diese Komponenten zuzugreifen, indem sie Funktionen/Strukturen/... mit dem Paket-/Modulnamen qualifizieren (z. B. `MyModule.run_this_task(...)`).

### Julia ⇔ C/C++: Quick reference

| Software Concept               | Julia                                                                          | C/C++                                                     |
|:------------------------------ |:------------------------------------------------------------------------------ |:--------------------------------------------------------- |
| unnamed scope                  | `begin` ... `end`                                                              | `{` ... `}`                                               |
| function scope                 | `function x()` ... `end`                                                       | `int x() {` ... `}`                                       |
| global scope                   | `module MyMod` ... `end`                                                       | `namespace MyNS {` ... `}`                                |
| software module                | A Julia "package"                                                              | `.h`/`.hpp` files<br>+compiled `somelib.a`                |
| assembling<br>software modules | `SomePkg.jl`: ...<br>`import("subfile1.jl")`<br>`import("subfile2.jl")`<br>... | `$(AR) *.o` &rArr; `somelib.a`                            |
| import<br>software module      | `import SomePkg`                                                               | `#include <somelib>`<br>+link in `somelib.a`              |
| module library                 | `LOAD_PATH[]`, *Git repository,<br>**custom package registry                   | more `.h`/`.hpp` files<br>+bigger compiled `somebiglib.a` |

* The Julia package manager supports registering multiple packages from a single Git repository.<br> * This allows users to house a library of related packages in a single repository.<br> ** Julia registries are primarily designed to provide versioning \& distribution of packages.<br> ** Custom package registries can be used to create a type of module library.

## Noteworthy differences from Common Lisp

  * Julia verwendet standardmäßig die 1-basierte Indizierung für Arrays und kann auch beliebige [index offsets](@ref man-custom-indices) verarbeiten.
  * Funktionen und Variablen teilen sich denselben Namensraum („Lisp-1“).
  * Es gibt einen [`Pair`](@ref) Typ, der jedoch nicht als `COMMON-LISP:CONS` verwendet werden soll. Verschiedene iterable Sammlungen können in den meisten Teilen der Sprache austauschbar verwendet werden (z. B. Splatting, Tupel usw.). `Tuple`s sind den Common Lisp-Listen für *kurze* Sammlungen heterogener Elemente am nächsten. Verwenden Sie `NamedTuple`s anstelle von Alists. Für größere Sammlungen homogener Typen sollten `Array`s und `Dict`s verwendet werden.
  * Der typische Julia-Workflow für Prototyping verwendet ebenfalls eine kontinuierliche Manipulation des Bildes, die mit dem [Revise.jl](https://github.com/timholy/Revise.jl)-Paket implementiert ist.
  * Für die Leistung bevorzugt Julia, dass Operationen [type stability](@ref man-type-stability) haben. Während Common Lisp von den zugrunde liegenden Maschinenoperationen abstrahiert, bleibt Julia näher an ihnen. Zum Beispiel:

      * Die ganzzahlige Division mit `/` gibt immer ein Fließkommaergebnis zurück, selbst wenn die Berechnung genau ist.

          * `//` gibt immer ein rationales Ergebnis zurück.
          * `÷` gibt immer ein (abgerundetes) ganzzahliges Ergebnis zurück
      * Bignums werden unterstützt, aber die Umwandlung erfolgt nicht automatisch; gewöhnliche Ganzzahlen [overflow](@ref faq-integer-arithmetic).
      * Komplexe Zahlen werden unterstützt, aber um komplexe Ergebnisse zu erhalten, [you need complex inputs](@ref faq-domain-errors).
      * Es gibt mehrere komplexe und rationale Typen mit unterschiedlichen Komponenten-Typen.
  * Module (Namespaces) können hierarchisch sein. [`import`](@ref) und [`using`](@ref) haben eine doppelte Rolle: Sie laden den Code und machen ihn im Namensraum verfügbar. `import` nur für den Modulnamen ist möglich (ungefähr gleichwertig zu `ASDF:LOAD-OP`). Slotnamen müssen nicht separat exportiert werden. Globale Variablen können von außerhalb des Moduls nicht zugewiesen werden (außer mit `eval(mod, :(var = val))` als Ausweg).
  * Makros beginnen mit `@` und sind nicht so nahtlos in die Sprache integriert wie in Common Lisp; folglich ist die Verwendung von Makros nicht so verbreitet wie im letzteren. Eine Form der Hygiene für [macros](@ref Metaprogramming) wird von der Sprache unterstützt. Aufgrund der unterschiedlichen Oberflächensyntax gibt es kein Äquivalent zu `COMMON-LISP:&BODY`.
  * *Alle* Funktionen sind generisch und verwenden mehrere Dispatches. Die Argumentlisten müssen nicht dem gleichen Template folgen, was zu einem leistungsstarken Idiom führt (siehe [`do`](@ref)). Optionale und Schlüsselwortargumente werden unterschiedlich behandelt. Methodenambiguitäten werden nicht wie im Common Lisp Object System gelöst, was die Definition einer spezifischeren Methode für die Schnittmenge erforderlich macht.
  * Symbole gehören zu keinem Paket und enthalten *an sich* keine Werte. `M.var` wertet das Symbol `var` im Modul `M` aus.
  * Ein funktionaler Programmierstil wird von der Sprache vollständig unterstützt, einschließlich Closures, ist jedoch nicht immer die idiomatische Lösung für Julia. Einige [workarounds](@ref man-performance-captured) können für die Leistung erforderlich sein, wenn erfasste Variablen geändert werden.
