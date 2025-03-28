# Dates

```@meta
DocTestSetup = :(using Dates)
```

Das `Dates`-Modul bietet zwei Typen zur Arbeit mit Daten: [`Date`](@ref) und [`DateTime`](@ref), die Tag- bzw. Millisekunden-Präzision darstellen; beide sind Untertypen des abstrakten [`TimeType`](@ref). Die Motivation für unterschiedliche Typen ist einfach: Einige Operationen sind viel einfacher, sowohl in Bezug auf den Code als auch auf das mentale Denken, wenn die Komplexitäten einer höheren Präzision nicht berücksichtigt werden müssen. Zum Beispiel, da der Typ `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` nur auf die Präzision eines einzelnen Datums (d.h. keine Stunden, Minuten oder Sekunden) auflöst, sind normale Überlegungen zu Zeitzonen, Sommerzeit und Schaltsekunden unnötig und werden vermieden.

Sowohl [`Date`](@ref) als auch [`DateTime`](@ref) sind im Grunde unveränderliche [`Int64`](@ref) Wrapper. Das einzelne `instant`-Feld beider Typen ist tatsächlich ein `UTInstant{P}`-Typ, der eine kontinuierlich steigende Maschinenzeitleiste basierend auf der UT-Sekunde [^1] darstellt. Der Typ `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` ist sich der Zeitzonen nicht bewusst (*naiv*, im Python-Jargon), analog zu einem *LocalDateTime* in Java 8. Zusätzliche Zeitzonenfunktionen können über die [TimeZones.jl package](https://github.com/JuliaTime/TimeZones.jl/) hinzugefügt werden, die die [IANA time zone database](https://www.iana.org/time-zones) kompiliert. Sowohl `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` als auch `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` basieren auf dem [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) Standard, der dem proleptischen Gregorianischen Kalender folgt. Eine Anmerkung ist, dass der ISO 8601 Standard besonders bezüglich BC/BCE-Daten ist. Im Allgemeinen folgte der letzte Tag der BC/BCE-Ära, der 31.12.1 v. Chr. (BC/BCE), dem 1.1.1 n. Chr. (AD/CE), sodass es kein Jahr null gibt. Der ISO-Standard besagt jedoch, dass 1 v. Chr. (BC/BCE) Jahr null ist, sodass `0000-12-31` der Tag vor `0001-01-01` ist, und Jahr `-0001` (ja, negativ eins für das Jahr) ist 2 v. Chr. (BC/BCE), Jahr `-0002` ist 3 v. Chr. (BC/BCE) usw.

[^1]: The notion of the UT second is actually quite fundamental. There are basically two different notions of time generally accepted, one based on the physical rotation of the earth (one full rotation = 1 day), the other based on the SI second (a fixed, constant value). These are radically different! Think about it, a "UT second", as defined relative to the rotation of the earth, may have a different absolute length depending on the day! Anyway, the fact that [`Date`](@ref) and [`DateTime`](@ref) are based on UT seconds is a simplifying, yet honest assumption so that things like leap seconds and all their complexity can be avoided. This basis of time is formally called [UT](https://en.wikipedia.org/wiki/Universal_Time) or UT1. Basing types on the UT second basically means that every minute has 60 seconds and every day has 24 hours and leads to more natural calculations when working with calendar dates.

## Constructors

[`Date`](@ref) und [`DateTime`](@ref) Typen können durch Ganzzahlen oder [`Period`](@ref) Typen, durch Parsen oder durch Anpassungen (mehr dazu später) konstruiert werden:

```jldoctest
julia> DateTime(2013)
2013-01-01T00:00:00

julia> DateTime(2013,7)
2013-07-01T00:00:00

julia> DateTime(2013,7,1)
2013-07-01T00:00:00

julia> DateTime(2013,7,1,12)
2013-07-01T12:00:00

julia> DateTime(2013,7,1,12,30)
2013-07-01T12:30:00

julia> DateTime(2013,7,1,12,30,59)
2013-07-01T12:30:59

julia> DateTime(2013,7,1,12,30,59,1)
2013-07-01T12:30:59.001

julia> Date(2013)
2013-01-01

julia> Date(2013,7)
2013-07-01

julia> Date(2013,7,1)
2013-07-01

julia> Date(Dates.Year(2013),Dates.Month(7),Dates.Day(1))
2013-07-01

julia> Date(Dates.Month(7),Dates.Year(2013))
2013-07-01
```

[`Date`](@ref) oder [`DateTime`](@ref) Parsing wird durch die Verwendung von Format-Strings erreicht. Format-Strings funktionieren nach dem Prinzip, *delimitierte* oder *feste Breite* "Slots" zu definieren, die einen Punkt zum Parsen enthalten, und den zu parsenden Text sowie den Format-String an einen `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` oder `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` Konstruktor zu übergeben, in der Form `Date("2015-01-01",dateformat"y-m-d")` oder `DateTime("20150101",dateformat"yyyymmdd")`.

Getrennte Slots werden markiert, indem der Trennzeichen angegeben wird, den der Parser zwischen zwei aufeinanderfolgenden Perioden erwarten soll; so lässt `"y-m-d"` den Parser wissen, dass zwischen dem ersten und zweiten Slot in einem Datumsstring wie `"2014-07-16"` das Zeichen `-` gefunden werden sollte. Die Zeichen `y`, `m` und `d` lassen den Parser wissen, welche Perioden in jedem Slot geparst werden sollen.

Wie im Fall der oben genannten Konstruktoren wie `Date(2013)` erlauben delimitierte `DateFormat`s fehlende Teile von Daten und Zeiten, solange die vorhergehenden Teile angegeben sind. Die anderen Teile erhalten die üblichen Standardwerte. Zum Beispiel gibt `Date("1981-03", dateformat"y-m-d")` `1981-03-01` zurück, während `Date("31/12", dateformat"d/m/y")` `0001-12-31` ergibt. (Beachten Sie, dass das Standardjahr 1 n. Chr. ist.) Ein leerer String wirft jedoch immer einen `ArgumentError`.

Feste Breiten-Slots werden durch das wiederholte Zeichen des Punktes in der Anzahl angegeben, die der Breite entspricht, ohne Trennzeichen zwischen den Zeichen. So würde `dateformat"yyyymmdd"` einem Datumsstring wie `"20140716"` entsprechen. Der Parser unterscheidet einen festen Breiten-Slot durch das Fehlen eines Trennzeichens und bemerkt den Übergang `"yyyymm"` von einem Punktzeichen zum nächsten.

Die Unterstützung für die Verarbeitung von Monatsnamen in Textform wird ebenfalls durch die Zeichen `u` und `U` unterstützt, für abgekürzte bzw. vollständige Monatsnamen. Standardmäßig werden nur englische Monatsnamen unterstützt, sodass `u` "Jan", "Feb", "Mar" usw. entspricht. Und `U` entspricht "Januar", "Februar", "März" usw. Ähnlich wie bei anderen Name=>Wert-Zuordnungsfunktionen [`dayname`](@ref) und [`monthname`](@ref) können benutzerdefinierte Lokalisierungen geladen werden, indem die Zuordnung `locale=>Dict{String,Int}` an die Diktate `MONTHTOVALUEABBR` und `MONTHTOVALUE` für abgekürzte bzw. vollständige Monatsnamen übergeben wird.

Die obigen Beispiele verwendeten das `dateformat""` String-Makro. Dieses Makro erstellt ein `DateFormat`-Objekt einmal, wenn das Makro erweitert wird, und verwendet dasselbe `DateFormat`-Objekt, selbst wenn ein Code-Snippet mehrmals ausgeführt wird.

```jldoctest
julia> for i = 1:10^5
           Date("2015-01-01", dateformat"y-m-d")
       end
```

Oder Sie können das DateFormat-Objekt explizit erstellen:

```jldoctest
julia> df = DateFormat("y-m-d");

julia> dt = Date("2015-01-01",df)
2015-01-01

julia> dt2 = Date("2015-01-02",df)
2015-01-02
```

Alternativ können Sie Broadcasting verwenden:

```jldoctest
julia> years = ["2015", "2016"];

julia> Date.(years, DateFormat("yyyy"))
2-element Vector{Date}:
 2015-01-01
 2016-01-01
```

Zur Bequemlichkeit können Sie den Format-String direkt übergeben (z. B. `Date("2015-01-01","y-m-d")`), obwohl diese Form Leistungskosten verursacht, wenn Sie dasselbe Format wiederholt analysieren, da intern jedes Mal ein neues `DateFormat`-Objekt erstellt wird.

Sowohl über die Konstruktoren als auch über die Funktionen kann ein `Date` oder `DateTime` aus Strings erstellt werden, indem die Funktionen [`parse`](@ref) und [`tryparse`](@ref) verwendet werden, jedoch mit einem optionalen dritten Argument vom Typ `DateFormat`, das das Format angibt; zum Beispiel `parse(Date, "06.23.2013", dateformat"m.d.y")` oder `tryparse(DateTime, "1999-12-31T23:59:59")`, das das Standardformat verwendet. Der bemerkenswerte Unterschied zwischen den Funktionen besteht darin, dass bei `4d61726b646f776e2e436f64652822222c202274727970617273652229_40726566` kein Fehler ausgelöst wird, wenn der String leer oder in einem ungültigen Format vorliegt; stattdessen wird `nothing` zurückgegeben.

!!! compat "Julia 1.9"
    Vor Julia 1.9 konnten leere Strings ohne Fehler an Konstruktoren und `parse` übergeben werden, was entsprechend `DateTime(1)`, `Date(1)` oder `Time(0)` zurückgab. Ebenso gab `tryparse` nicht `nothing` zurück.


Eine vollständige Suite von Parsing- und Formatierungstests sowie Beispielen ist verfügbar in [`stdlib/Dates/test/io.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/io.jl).

## Durations/Comparisons

Die Bestimmung der Zeitspanne zwischen zwei [`Date`](@ref) oder [`DateTime`](@ref) ist einfach, wenn man ihre zugrunde liegende Darstellung als `UTInstant{Day}` und `UTInstant{Millisecond}` betrachtet. Der Unterschied zwischen `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` wird in der Anzahl von [`Day`](@ref) zurückgegeben, und `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` in der Anzahl von [`Millisecond`](@ref). Ebenso ist der Vergleich von [`TimeType`](@ref) eine einfache Angelegenheit des Vergleichs der zugrunde liegenden Maschineninstanzen (die wiederum die internen [`Int64`](@ref) Werte vergleicht).

```jldoctest
julia> dt = Date(2012,2,29)
2012-02-29

julia> dt2 = Date(2000,2,1)
2000-02-01

julia> dump(dt)
Date
  instant: Dates.UTInstant{Day}
    periods: Day
      value: Int64 734562

julia> dump(dt2)
Date
  instant: Dates.UTInstant{Day}
    periods: Day
      value: Int64 730151

julia> dt > dt2
true

julia> dt != dt2
true

julia> dt + dt2
ERROR: MethodError: no method matching +(::Date, ::Date)
[...]

julia> dt * dt2
ERROR: MethodError: no method matching *(::Date, ::Date)
[...]

julia> dt / dt2
ERROR: MethodError: no method matching /(::Date, ::Date)

julia> dt - dt2
4411 days

julia> dt2 - dt
-4411 days

julia> dt = DateTime(2012,2,29)
2012-02-29T00:00:00

julia> dt2 = DateTime(2000,2,1)
2000-02-01T00:00:00

julia> dt - dt2
381110400000 milliseconds
```

## Accessor Functions

Weil die [`Date`](@ref) und [`DateTime`](@ref) Typen als einzelne [`Int64`](@ref) Werte gespeichert werden, können Datenteile oder Felder über Zugriffs-Funktionen abgerufen werden. Die Kleinbuchstaben-Zugriffs-Funktionen geben das Feld als Ganzzahl zurück:

```jldoctest tdate
julia> t = Date(2014, 1, 31)
2014-01-31

julia> Dates.year(t)
2014

julia> Dates.month(t)
1

julia> Dates.week(t)
5

julia> Dates.day(t)
31
```

While propercase return the same value in the corresponding [`Period`](@ref) type:

```jldoctest tdate
julia> Dates.Year(t)
2014 years

julia> Dates.Day(t)
31 days
```

Kombinationsmethoden werden bereitgestellt, da es effizienter ist, mehrere Felder gleichzeitig als einzeln zuzugreifen:

```jldoctest tdate
julia> Dates.yearmonth(t)
(2014, 1)

julia> Dates.monthday(t)
(1, 31)

julia> Dates.yearmonthday(t)
(2014, 1, 31)
```

Man kann auch auf den zugrunde liegenden `UTInstant` oder den ganzzahligen Wert zugreifen:

```jldoctest tdate
julia> dump(t)
Date
  instant: Dates.UTInstant{Day}
    periods: Day
      value: Int64 735264

julia> t.instant
Dates.UTInstant{Day}(Day(735264))

julia> Dates.value(t)
735264
```

## Query Functions

Abfragefunktionen bieten kalendarische Informationen über ein [`TimeType`](@ref). Sie enthalten Informationen über den Wochentag:

```jldoctest tdate2
julia> t = Date(2014, 1, 31)
2014-01-31

julia> Dates.dayofweek(t)
5

julia> Dates.dayname(t)
"Friday"

julia> Dates.dayofweekofmonth(t) # 5th Friday of January
5
```

Monat des Jahres:

```jldoctest tdate2
julia> Dates.monthname(t)
"January"

julia> Dates.daysinmonth(t)
31
```

Ebenso wie Informationen über das Jahr und das Quartal von der [`TimeType`](@ref):

```jldoctest tdate2
julia> Dates.isleapyear(t)
false

julia> Dates.dayofyear(t)
31

julia> Dates.quarterofyear(t)
1

julia> Dates.dayofquarter(t)
31
```

Die [`dayname`](@ref) und [`monthname`](@ref) Methoden können auch ein optionales `locale` Schlüsselwort annehmen, das verwendet werden kann, um den Namen des Tages oder Monats des Jahres für andere Sprachen/Regionen zurückzugeben. Es gibt auch Versionen dieser Funktionen, die die abgekürzten Namen zurückgeben, nämlich [`dayabbr`](@ref) und [`monthabbr`](@ref). Zuerst wird die Zuordnung in die `LOCALES` Variable geladen:

```jldoctest tdate2
julia> french_months = ["janvier", "février", "mars", "avril", "mai", "juin",
                        "juillet", "août", "septembre", "octobre", "novembre", "décembre"];

julia> french_months_abbrev = ["janv","févr","mars","avril","mai","juin",
                              "juil","août","sept","oct","nov","déc"];

julia> french_days = ["lundi","mardi","mercredi","jeudi","vendredi","samedi","dimanche"];

julia> Dates.LOCALES["french"] = Dates.DateLocale(french_months, french_months_abbrev, french_days, [""]);
```

Die oben genannten Funktionen können dann verwendet werden, um die Abfragen durchzuführen:

```jldoctest tdate2
julia> Dates.dayname(t;locale="french")
"vendredi"

julia> Dates.monthname(t;locale="french")
"janvier"

julia> Dates.monthabbr(t;locale="french")
"janv"
```

Da die abgekürzten Versionen der Tage nicht geladen sind, wird der Versuch, die Funktion `dayabbr` zu verwenden, einen Fehler auslösen.

```jldoctest tdate2
julia> Dates.dayabbr(t;locale="french")
ERROR: BoundsError: attempt to access 1-element Vector{String} at index [5]
Stacktrace:
[...]
```

## TimeType-Period Arithmetic

Es ist eine gute Praxis, sich mit der Handhabung von Datums- und Zeitarithmetik in jedem Sprach-/Datumsrahmen vertraut zu machen, da es einige [tricky issues](https://codeblog.jonskeet.uk/2010/12/01/the-joys-of-date-time-arithmetic/) zu berücksichtigen gibt (obwohl dies bei Datentypen mit Tagesgenauigkeit viel weniger der Fall ist).

Das `Dates`-Modul versucht, dem einfachen Prinzip zu folgen, so wenig wie möglich zu ändern, wenn es um [`Period`](@ref)-Arithmetik geht. Dieser Ansatz ist auch oft als *kalendermäßige* Arithmetik bekannt oder was Sie wahrscheinlich erraten würden, wenn jemand Sie in einem Gespräch nach derselben Berechnung fragen würde. Warum all der Aufruhr darüber? Lassen Sie uns ein klassisches Beispiel nehmen: Fügen Sie dem 31. Januar 2014 1 Monat hinzu. Was ist die Antwort? Javascript wird [March 3](https://markhneedham.com/blog/2009/01/07/javascript-add-a-month-to-a-date/) sagen (geht von 31 Tagen aus). PHP sagt [March 2](https://stackoverflow.com/questions/5760262/php-adding-months-to-a-date-while-not-exceeding-the-last-day-of-the-month) (geht von 30 Tagen aus). Die Tatsache ist, dass es keine richtige Antwort gibt. Im `Dates`-Modul ergibt sich das Ergebnis des 28. Februar. Wie kommt es dazu? Betrachten Sie das klassische 7-7-7 Glücksspielspiel in Casinos.

Stellen Sie sich nun vor, dass anstelle von 7-7-7 die Slots Jahr-Monat-Tag sind, oder in unserem Beispiel, 2014-01-31. Wenn Sie zu diesem Datum 1 Monat hinzufügen möchten, wird der Monatsslot erhöht, sodass wir jetzt 2014-02-31 haben. Dann wird die Tageszahl überprüft, ob sie größer ist als der letzte gültige Tag des neuen Monats; wenn dies der Fall ist (wie im obigen Fall), wird die Tageszahl auf den letzten gültigen Tag (28) angepasst. Was sind die Folgen dieses Ansatzes? Gehen Sie voran und fügen Sie einen weiteren Monat zu unserem Datum hinzu, `2014-02-28 + Monat(1) == 2014-03-28`. Was? Haben Sie den letzten Tag im März erwartet? Nein, tut mir leid, denken Sie an die 7-7-7-Slots. So wenige Slots wie möglich werden sich ändern, also erhöhen wir zuerst den Monatsslot um 1, 2014-03-28, und boom, wir sind fertig, weil das ein gültiges Datum ist. Andererseits, wenn wir 2 Monate zu unserem ursprünglichen Datum, 2014-01-31, hinzufügen würden, würden wir 2014-03-31 erhalten, wie erwartet. Die andere Folge dieses Ansatzes ist ein Verlust der Assoziativität, wenn eine bestimmte Reihenfolge erzwungen wird (d.h. das Hinzufügen von Dingen in unterschiedlichen Reihenfolgen führt zu unterschiedlichen Ergebnissen). Zum Beispiel:

```jldoctest
julia> (Date(2014,1,29)+Dates.Day(1)) + Dates.Month(1)
2014-02-28

julia> (Date(2014,1,29)+Dates.Month(1)) + Dates.Day(1)
2014-03-01
```

Was passiert dort? In der ersten Zeile fügen wir 1 Tag zum 29. Januar hinzu, was zu 2014-01-30 führt; dann fügen wir 1 Monat hinzu, sodass wir 2014-02-30 erhalten, was dann auf 2014-02-28 angepasst wird. Im zweiten Beispiel fügen wir zuerst 1 Monat hinzu, wo wir 2014-02-29 erhalten, was auf 2014-02-28 angepasst wird, und *dann* fügen wir 1 Tag hinzu, was zu 2014-03-01 führt. Ein Designprinzip, das in diesem Fall hilft, ist, dass bei mehreren Perioden die Operationen nach den *Typen* der Perioden und nicht nach ihrem Wert oder ihrer Position angeordnet werden; das bedeutet, dass `Jahr` immer zuerst hinzugefügt wird, dann `Monat`, dann `Woche` usw. Daher führt das Folgende zu Assoziativität und funktioniert einfach:

```jldoctest
julia> Date(2014,1,29) + Dates.Day(1) + Dates.Month(1)
2014-03-01

julia> Date(2014,1,29) + Dates.Month(1) + Dates.Day(1)
2014-03-01
```

Tricky? Vielleicht. Was soll ein unschuldiger `Dates`-Benutzer tun? Die Quintessenz ist, sich bewusst zu sein, dass das explizite Erzwingen einer bestimmten Assoziativität beim Umgang mit Monaten zu unerwarteten Ergebnissen führen kann, aber ansonsten sollte alles wie erwartet funktionieren. Glücklicherweise ist das so ziemlich das Ausmaß der seltsamen Fälle in der Datums-Perioden-Arithmetik beim Umgang mit Zeit in UT (und die "Freuden" des Umgangs mit Sommerzeit, Schaltsekunden usw. zu vermeiden).

Als Bonus funktionieren alle Zeitarithmetik-Objekte direkt mit Bereichen:

```jldoctest
julia> dr = Date(2014,1,29):Day(1):Date(2014,2,3)
Date("2014-01-29"):Day(1):Date("2014-02-03")

julia> collect(dr)
6-element Vector{Date}:
 2014-01-29
 2014-01-30
 2014-01-31
 2014-02-01
 2014-02-02
 2014-02-03

julia> dr = Date(2014,1,29):Dates.Month(1):Date(2014,07,29)
Date("2014-01-29"):Month(1):Date("2014-07-29")

julia> collect(dr)
7-element Vector{Date}:
 2014-01-29
 2014-02-28
 2014-03-29
 2014-04-29
 2014-05-29
 2014-06-29
 2014-07-29
```

## Adjuster Functions

So praktisch die Datumsarithmetik auch ist, oft haben die Arten von Berechnungen, die für Daten benötigt werden, eine *kalendermäßige* oder *temporale* Natur, anstatt eine feste Anzahl von Perioden. Feiertage sind ein perfektes Beispiel; die meisten folgen Regeln wie "Memorial Day = Letzter Montag im Mai" oder "Thanksgiving = 4. Donnerstag im November". Diese Arten von temporalen Ausdrücken befassen sich mit Regeln, die relativ zum Kalender sind, wie erster oder letzter des Monats, nächster Dienstag oder die ersten und dritten Mittwoche usw.

Das `Dates`-Modul bietet die *Adjuster*-API über mehrere praktische Methoden, die dabei helfen, zeitliche Regeln einfach und prägnant auszudrücken. Die erste Gruppe von Adjuster-Methoden befasst sich mit dem ersten und letzten Tag von Wochen, Monaten, Quartalen und Jahren. Sie nehmen jeweils einen einzelnen [`TimeType`](@ref) als Eingabe und geben den ersten oder letzten Tag des gewünschten Zeitraums relativ zur Eingabe zurück oder *passen sich an*.

```jldoctest
julia> Dates.firstdayofweek(Date(2014,7,16)) # Adjusts the input to the Monday of the input's week
2014-07-14

julia> Dates.lastdayofmonth(Date(2014,7,16)) # Adjusts to the last day of the input's month
2014-07-31

julia> Dates.lastdayofquarter(Date(2014,7,16)) # Adjusts to the last day of the input's quarter
2014-09-30
```

Die nächsten beiden höherwertigen Methoden, [`tonext`](@ref) und [`toprev`](@ref), verallgemeinern die Arbeit mit zeitlichen Ausdrücken, indem sie eine `DateFunction` als erstes Argument verwenden, zusammen mit einem Start-[`TimeType`](@ref). Eine `DateFunction` ist einfach eine Funktion, normalerweise anonym, die ein einzelnes `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566` als Eingabe nimmt und ein [`Bool`](@ref) zurückgibt, wobei `true` ein erfülltes Anpassungskriterium anzeigt. Zum Beispiel:

```jldoctest
julia> istuesday = x->Dates.dayofweek(x) == Dates.Tuesday; # Returns true if the day of the week of x is Tuesday

julia> Dates.tonext(istuesday, Date(2014,7,13)) # 2014-07-13 is a Sunday
2014-07-15

julia> Dates.tonext(Date(2014,7,13), Dates.Tuesday) # Convenience method provided for day of the week adjustments
2014-07-15
```

Dies ist nützlich mit der do-Block-Syntax für komplexere zeitliche Ausdrücke:

```jldoctest
julia> Dates.tonext(Date(2014,7,13)) do x
           # Return true on the 4th Thursday of November (Thanksgiving)
           Dates.dayofweek(x) == Dates.Thursday &&
           Dates.dayofweekofmonth(x) == 4 &&
           Dates.month(x) == Dates.November
       end
2014-11-27
```

Die [`Base.filter`](@ref) Methode kann verwendet werden, um alle gültigen Daten/Momente in einem bestimmten Bereich zu erhalten:

```jldoctest
# Pittsburgh street cleaning; Every 2nd Tuesday from April to November
# Date range from January 1st, 2014 to January 1st, 2015
julia> dr = Dates.Date(2014):Day(1):Dates.Date(2015);

julia> filter(dr) do x
           Dates.dayofweek(x) == Dates.Tue &&
           Dates.April <= Dates.month(x) <= Dates.Nov &&
           Dates.dayofweekofmonth(x) == 2
       end
8-element Vector{Date}:
 2014-04-08
 2014-05-13
 2014-06-10
 2014-07-08
 2014-08-12
 2014-09-09
 2014-10-14
 2014-11-11
```

Zusätzliche Beispiele und Tests sind verfügbar in [`stdlib/Dates/test/adjusters.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/adjusters.jl).

## Period Types

Perioden sind eine menschliche Sicht auf diskrete, manchmal unregelmäßige Zeitdauern. Betrachten Sie 1 Monat; er könnte in Tagen einen Wert von 28, 29, 30 oder 31 darstellen, abhängig vom Jahr und Kontext des Monats. Oder ein Jahr könnte 365 oder 366 Tage im Falle eines Schaltjahres darstellen. [`Period`](@ref)-Typen sind einfache [`Int64`](@ref)-Wrapper und werden erstellt, indem man jeden `Int64`-konvertierbaren Typ umschließt, d.h. `Year(1)` oder `Month(3.0)`. Arithmetik zwischen `4d61726b646f776e2e436f64652822222c2022506572696f642229_40726566` des gleichen Typs verhält sich wie ganze Zahlen, und eine begrenzte `Period-Real`-Arithmetik ist verfügbar. Sie können die zugrunde liegende ganze Zahl mit [`Dates.value`](@ref) extrahieren.

```jldoctest
julia> y1 = Dates.Year(1)
1 year

julia> y2 = Dates.Year(2)
2 years

julia> y3 = Dates.Year(10)
10 years

julia> y1 + y2
3 years

julia> div(y3,y2)
5

julia> y3 - y2
8 years

julia> y3 % y2
0 years

julia> div(y3,3) # mirrors integer division
3 years

julia> Dates.value(Dates.Millisecond(10))
10
```

Die Darstellung von Zeiträumen oder Dauern, die keine ganzzahligen Vielfachen der grundlegenden Typen sind, kann mit dem [`Dates.CompoundPeriod`](@ref)-Typ erreicht werden. Zusammengesetzte Zeiträume können manuell aus einfachen [`Period`](@ref)-Typen erstellt werden. Darüber hinaus kann die [`canonicalize`](@ref)-Funktion verwendet werden, um einen Zeitraum in einen `4d61726b646f776e2e436f64652822222c202244617465732e436f6d706f756e64506572696f642229_40726566` zu zerlegen. Dies ist besonders nützlich, um eine Dauer, z. B. eine Differenz von zwei `DateTime`, in eine praktischere Darstellung zu konvertieren.

```jldoctest
julia> cp = Dates.CompoundPeriod(Day(1),Minute(1))
1 day, 1 minute

julia> t1 = DateTime(2018,8,8,16,58,00)
2018-08-08T16:58:00

julia> t2 = DateTime(2021,6,23,10,00,00)
2021-06-23T10:00:00

julia> canonicalize(t2-t1) # creates a CompoundPeriod
149 weeks, 6 days, 17 hours, 2 minutes
```

## Rounding

[`Date`](@ref) und [`DateTime`](@ref) Werte können auf eine bestimmte Auflösung (z. B. 1 Monat oder 15 Minuten) gerundet werden mit [`floor`](@ref), [`ceil`](@ref) oder [`round`](@ref):

```jldoctest
julia> floor(Date(1985, 8, 16), Dates.Month)
1985-08-01

julia> ceil(DateTime(2013, 2, 13, 0, 31, 20), Dates.Minute(15))
2013-02-13T00:45:00

julia> round(DateTime(2016, 8, 6, 20, 15), Dates.Day)
2016-08-07T00:00:00
```

Im Gegensatz zur numerischen [`round`](@ref) Methode, die standardmäßig bei Gleichständen zur geraden Zahl tendiert, verwendet die [`TimeType`](@ref)`4d61726b646f776e2e436f64652822222c2022726f756e642229_40726566` Methode den Rundungsmodus `RoundNearestTiesUp`. (Es ist schwierig zu erraten, was das Brechen von Gleichständen zur nächsten "geraden" `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566` bedeuten würde.) Weitere Details zu den verfügbaren `RoundingMode` s finden Sie in der [API reference](@ref stdlib-dates-api).

Das Runden sollte im Allgemeinen wie erwartet funktionieren, aber es gibt einige Fälle, in denen das erwartete Verhalten nicht offensichtlich ist.

### Rounding Epoch

In vielen Fällen teilt die für das Runden angegebene Auflösung (z. B. `Dates.Second(30)`) gleichmäßig in den nächstgrößeren Zeitraum (in diesem Fall `Dates.Minute(1)`). Das Rundungsverhalten in Fällen, in denen dies nicht zutrifft, kann jedoch zu Verwirrung führen. Was ist das erwartete Ergebnis des Rundens von [`DateTime`](@ref) auf die nächsten 10 Stunden?

```jldoctest
julia> round(DateTime(2016, 7, 17, 11, 55), Dates.Hour(10))
2016-07-17T12:00:00
```

Das mag verwirrend erscheinen, da die Stunde (12) nicht durch 10 teilbar ist. Der Grund, warum `2016-07-17T12:00:00` gewählt wurde, ist, dass es 17.676.660 Stunden nach `0000-01-01T00:00:00` ist, und 17.676.660 ist durch 10 teilbar.

Da Julia [`Date`](@ref) und [`DateTime`](@ref) Werte gemäß dem ISO 8601 Standard dargestellt werden, wurde `0000-01-01T00:00:00` als Basis (oder "Rundungs-Epoche") gewählt, von der aus die Zählung der Tage (und Millisekunden) für Rundungsberechnungen beginnt. (Beachten Sie, dass dies leicht von Julias interner Darstellung von `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` abweicht, die [Rata Die notation](https://en.wikipedia.org/wiki/Rata_Die) verwendet; aber da der ISO 8601 Standard für den Endbenutzer am sichtbarsten ist, wurde `0000-01-01T00:00:00` als Rundungs-Epoche gewählt, anstelle des intern verwendeten `0000-12-31T00:00:00`, um Verwirrung zu minimieren.)

Die einzige Ausnahme von der Verwendung von `0000-01-01T00:00:00` als Rundungs-Epoche ist das Runden auf Wochen. Das Runden auf die nächste Woche gibt immer einen Montag zurück (den ersten Tag der Woche, wie von ISO 8601 festgelegt). Aus diesem Grund verwenden wir `0000-01-03T00:00:00` (den ersten Tag der ersten Woche des Jahres 0000, wie von ISO 8601 definiert) als Basis, wenn wir auf eine Anzahl von Wochen runden.

Hier ist ein verwandter Fall, in dem das erwartete Verhalten nicht unbedingt offensichtlich ist: Was passiert, wenn wir auf das nächste `P(2)` runden, wobei `P` ein [`Period`](@ref)-Typ ist? In einigen Fällen (insbesondere, wenn `P <: Dates.TimePeriod`) ist die Antwort klar:

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Hour(2))
2016-07-17T08:00:00

julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Minute(2))
2016-07-17T08:56:00
```

Das scheint offensichtlich zu sein, da zwei von jedem dieser Zeiträume immer noch gleichmäßig in den nächsten größeren Ordnungszeitraum unterteilt werden. Aber im Fall von zwei Monaten (die immer noch gleichmäßig in ein Jahr unterteilt werden) könnte die Antwort überraschend sein:

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Month(2))
2016-07-01T00:00:00
```

Warum auf den ersten Tag im Juli runden, obwohl es der Monat 7 (eine ungerade Zahl) ist? Der Schlüssel ist, dass Monate 1-indiziert sind (der erste Monat wird mit 1 zugewiesen), im Gegensatz zu Stunden, Minuten, Sekunden und Millisekunden (die erste davon wird mit 0 zugewiesen).

Das bedeutet, dass das Runden eines [`DateTime`](@ref) auf ein gerades Vielfaches von Sekunden, Minuten, Stunden oder Jahren (da die ISO 8601-Spezifikation ein Jahr null umfasst) zu einem `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` mit einem geraden Wert in diesem Feld führen wird, während das Runden eines `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` auf ein gerades Vielfaches von Monaten dazu führen wird, dass das Monatsfeld einen ungeraden Wert hat. Da sowohl Monate als auch Jahre eine unregelmäßige Anzahl von Tagen enthalten können, ist ungewiss, ob das Runden auf eine gerade Anzahl von Tagen zu einem geraden Wert im Tagesfeld führen wird.

Siehe die [API reference](@ref stdlib-dates-api) für zusätzliche Informationen zu den Methoden, die aus dem `Dates`-Modul exportiert werden.

## [API reference](@id stdlib-dates-api)

### Dates and Time Types

```@docs
Dates.Period
Dates.CompoundPeriod
Dates.Instant
Dates.UTInstant
Dates.TimeType
Dates.DateTime
Dates.Date
Dates.Time
Dates.TimeZone
Dates.UTC
```

### Dates Functions

```@docs
Dates.DateTime(::Int64, ::Int64, ::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
Dates.DateTime(::Dates.Period)
Dates.DateTime(::Function, ::Any...)
Dates.DateTime(::Dates.TimeType)
Dates.DateTime(::AbstractString, ::AbstractString)
Dates.format(::Dates.TimeType, ::AbstractString)
Dates.DateFormat
Dates.@dateformat_str
Dates.DateTime(::AbstractString, ::Dates.DateFormat)
Dates.Date(::Int64, ::Int64, ::Int64)
Dates.Date(::Dates.Period)
Dates.Date(::Function, ::Any, ::Any, ::Any)
Dates.Date(::Dates.TimeType)
Dates.Date(::AbstractString, ::AbstractString)
Dates.Date(::AbstractString, ::Dates.DateFormat)
Dates.Time(::Int64::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
Dates.Time(::Dates.TimePeriod)
Dates.Time(::Function, ::Any...)
Dates.Time(::Dates.DateTime)
Dates.Time(::AbstractString, ::AbstractString)
Dates.Time(::AbstractString, ::Dates.DateFormat)
Dates.now()
Dates.now(::Type{Dates.UTC})
Base.eps(::Union{Type{DateTime}, Type{Date}, Type{Time}, TimeType})
```

#### Accessor Functions

```@docs
Dates.year
Dates.month
Dates.week
Dates.day
Dates.hour
Dates.minute
Dates.second
Dates.millisecond
Dates.microsecond
Dates.nanosecond
Dates.Year(::Dates.TimeType)
Dates.Month(::Dates.TimeType)
Dates.Week(::Dates.TimeType)
Dates.Day(::Dates.TimeType)
Dates.Hour(::DateTime)
Dates.Minute(::DateTime)
Dates.Second(::DateTime)
Dates.Millisecond(::DateTime)
Dates.Microsecond(::Dates.Time)
Dates.Nanosecond(::Dates.Time)
Dates.yearmonth
Dates.monthday
Dates.yearmonthday
```

#### Query Functions

```@docs
Dates.dayname
Dates.dayabbr
Dates.dayofweek
Dates.dayofmonth
Dates.dayofweekofmonth
Dates.daysofweekinmonth
Dates.monthname
Dates.monthabbr
Dates.daysinmonth
Dates.isleapyear
Dates.dayofyear
Dates.daysinyear
Dates.quarterofyear
Dates.dayofquarter
```

#### Adjuster Functions

```@docs
Base.trunc(::Dates.TimeType, ::Type{Dates.Period})
Dates.firstdayofweek
Dates.lastdayofweek
Dates.firstdayofmonth
Dates.lastdayofmonth
Dates.firstdayofyear
Dates.lastdayofyear
Dates.firstdayofquarter
Dates.lastdayofquarter
Dates.tonext(::Dates.TimeType, ::Int)
Dates.toprev(::Dates.TimeType, ::Int)
Dates.tofirst
Dates.tolast
Dates.tonext(::Function, ::Dates.TimeType)
Dates.toprev(::Function, ::Dates.TimeType)
```

#### Periods

```@docs
Dates.Period(::Any)
Dates.CompoundPeriod(::Vector{<:Dates.Period})
Dates.canonicalize
Dates.value
Dates.default
Dates.periods
```

#### Rounding Functions

`Datum` und `DatumZeit` Werte können auf eine bestimmte Auflösung (z. B. 1 Monat oder 15 Minuten) mit `floor`, `ceil` oder `round` gerundet werden.

```@docs
Base.floor(::Dates.TimeType, ::Dates.Period)
Base.ceil(::Dates.TimeType, ::Dates.Period)
Base.round(::Dates.TimeType, ::Dates.Period, ::RoundingMode{:NearestTiesUp})
```

Die meisten `Period`-Werte können auch auf eine bestimmte Auflösung gerundet werden:

```@docs
Base.floor(::Dates.ConvertiblePeriod, ::T) where T <: Dates.ConvertiblePeriod
Base.ceil(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod)
Base.round(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod, ::RoundingMode{:NearestTiesUp})
```

Die folgenden Funktionen werden nicht exportiert:

```@docs
Dates.floorceil
Dates.epochdays2date
Dates.epochms2datetime
Dates.date2epochdays
Dates.datetime2epochms
```

#### Conversion Functions

```@docs
Dates.today
Dates.unix2datetime
Dates.datetime2unix
Dates.julian2datetime
Dates.datetime2julian
Dates.rata2datetime
Dates.datetime2rata
```

### Constants

Wochentage:

| Variable    | Abbr. | Value (Int) |
|:----------- |:----- |:----------- |
| `Monday`    | `Mon` | 1           |
| `Tuesday`   | `Tue` | 2           |
| `Wednesday` | `Wed` | 3           |
| `Thursday`  | `Thu` | 4           |
| `Friday`    | `Fri` | 5           |
| `Saturday`  | `Sat` | 6           |
| `Sunday`    | `Sun` | 7           |

Monate des Jahres:

| Variable    | Abbr. | Value (Int) |
|:----------- |:----- |:----------- |
| `January`   | `Jan` | 1           |
| `February`  | `Feb` | 2           |
| `March`     | `Mar` | 3           |
| `April`     | `Apr` | 4           |
| `May`       | `May` | 5           |
| `June`      | `Jun` | 6           |
| `July`      | `Jul` | 7           |
| `August`    | `Aug` | 8           |
| `September` | `Sep` | 9           |
| `October`   | `Oct` | 10          |
| `November`  | `Nov` | 11          |
| `December`  | `Dec` | 12          |

#### Common Date Formatters

```@docs
ISODateTimeFormat
ISODateFormat
ISOTimeFormat
RFC1123Format
```

```@meta
DocTestSetup = nothing
```
