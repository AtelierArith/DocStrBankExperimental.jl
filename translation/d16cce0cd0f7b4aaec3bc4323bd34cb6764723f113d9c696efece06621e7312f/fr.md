# Dates

```@meta
DocTestSetup = :(using Dates)
```

Le module `Dates` fournit deux types pour travailler avec des dates : [`Date`](@ref) et [`DateTime`](@ref), représentant respectivement la précision au jour et à la milliseconde ; les deux sont des sous-types de l'abstrait [`TimeType`](@ref). La motivation pour des types distincts est simple : certaines opérations sont beaucoup plus simples, tant en termes de code que de raisonnement mental, lorsque les complexités d'une plus grande précision n'ont pas à être prises en compte. Par exemple, puisque le type `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` ne se résout qu'à la précision d'une seule date (c'est-à-dire sans heures, minutes ou secondes), les considérations normales pour les fuseaux horaires, l'heure d'été et les secondes intercalaires sont inutiles et évitées.

Les types [`Date`](@ref) et [`DateTime`](@ref) sont essentiellement des wrappers immuables [`Int64`](@ref). Le champ unique `instant` de l'un ou l'autre type est en réalité un type `UTInstant{P}`, qui représente une chronologie machine en constante augmentation basée sur la seconde UT [^1]. Le type `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` n'est pas conscient des fuseaux horaires (*naïf*, en termes de Python), analogue à un *LocalDateTime* en Java 8. Une fonctionnalité de fuseau horaire supplémentaire peut être ajoutée via le [TimeZones.jl package](https://github.com/JuliaTime/TimeZones.jl/), qui compile le [IANA time zone database](https://www.iana.org/time-zones). Les types `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` et `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` sont basés sur la norme [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601), qui suit le calendrier grégorien proleptique. Une note est que la norme ISO 8601 est particulière concernant les dates avant notre ère (BC/BCE). En général, le dernier jour de l'ère BC/BCE, le 31-12-1 BC/BCE, a été suivi par le 1-1-1 AD/CE, donc il n'existe pas d'année zéro. Cependant, la norme ISO stipule que 1 BC/BCE est l'année zéro, donc `0000-12-31` est le jour avant `0001-01-01`, et l'année `-0001` (oui, moins un pour l'année) est 2 BC/BCE, l'année `-0002` est 3 BC/BCE, etc.

[^1]: The notion of the UT second is actually quite fundamental. There are basically two different notions of time generally accepted, one based on the physical rotation of the earth (one full rotation = 1 day), the other based on the SI second (a fixed, constant value). These are radically different! Think about it, a "UT second", as defined relative to the rotation of the earth, may have a different absolute length depending on the day! Anyway, the fact that [`Date`](@ref) and [`DateTime`](@ref) are based on UT seconds is a simplifying, yet honest assumption so that things like leap seconds and all their complexity can be avoided. This basis of time is formally called [UT](https://en.wikipedia.org/wiki/Universal_Time) or UT1. Basing types on the UT second basically means that every minute has 60 seconds and every day has 24 hours and leads to more natural calculations when working with calendar dates.

## Constructors

[`Date`](@ref) et [`DateTime`](@ref) peuvent être construits par des types entiers ou [`Period`](@ref), par analyse, ou par le biais d'ajusteurs (plus d'informations à ce sujet plus tard) :

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

[`Date`](@ref) ou [`DateTime`](@ref) le parsing est accompli par l'utilisation de chaînes de format. Les chaînes de format fonctionnent sur la notion de définir des "emplacements" *délimités* ou *de largeur fixe* qui contiennent un point à analyser et en passant le texte à analyser et la chaîne de format à un constructeur `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` ou `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566`, de la forme `Date("2015-01-01",dateformat"y-m-d")` ou `DateTime("20150101",dateformat"yyyymmdd")`.

Les emplacements délimités sont marqués en spécifiant le délimiteur que le parseur doit s'attendre entre deux périodes successives ; ainsi, `"y-m-d"` indique au parseur qu'entre le premier et le deuxième emplacement dans une chaîne de date comme `"2014-07-16"`, il doit trouver le caractère `-`. Les caractères `y`, `m` et `d` informent le parseur des périodes à analyser dans chaque emplacement.

Comme dans le cas des constructeurs ci-dessus tels que `Date(2013)`, les `DateFormat` délimités permettent des parties manquantes de dates et d'heures tant que les parties précédentes sont fournies. Les autres parties reçoivent les valeurs par défaut habituelles. Par exemple, `Date("1981-03", dateformat"y-m-d")` renvoie `1981-03-01`, tandis que `Date("31/12", dateformat"d/m/y")` donne `0001-12-31`. (Notez que l'année par défaut est 1 de notre ère/CE.) Cependant, une chaîne vide lance toujours une `ArgumentError`.

Les emplacements à largeur fixe sont spécifiés en répétant le caractère point le nombre de fois correspondant à la largeur sans délimiteur entre les caractères. Ainsi, `dateformat"yyyymmdd"` correspondrait à une chaîne de date comme `"20140716"`. Le parseur distingue un emplacement à largeur fixe par l'absence de délimiteur, notant la transition `"yyyymm"` d'un caractère point au suivant.

Le support pour l'analyse des mois au format texte est également pris en charge grâce aux caractères `u` et `U`, pour les noms de mois abrégés et complets, respectivement. Par défaut, seuls les noms de mois en anglais sont pris en charge, donc `u` correspond à "Jan", "Feb", "Mar", etc. Et `U` correspond à "January", "February", "March", etc. Semblable à d'autres fonctions de mappage nom=>valeur [`dayname`](@ref) et [`monthname`](@ref), des locales personnalisées peuvent être chargées en passant le mappage `locale=>Dict{String,Int}` aux dictionnaires `MONTHTOVALUEABBR` et `MONTHTOVALUE` pour les noms de mois abrégés et complets, respectivement.

Les exemples ci-dessus ont utilisé la macro de chaîne `dateformat""`. Cette macro crée un objet `DateFormat` une fois lorsque la macro est développée et utilise le même objet `DateFormat` même si un extrait de code est exécuté plusieurs fois.

```jldoctest
julia> for i = 1:10^5
           Date("2015-01-01", dateformat"y-m-d")
       end
```

Ou vous pouvez créer l'objet DateFormat explicitement :

```jldoctest
julia> df = DateFormat("y-m-d");

julia> dt = Date("2015-01-01",df)
2015-01-01

julia> dt2 = Date("2015-01-02",df)
2015-01-02
```

Alternativement, utilisez la diffusion :

```jldoctest
julia> years = ["2015", "2016"];

julia> Date.(years, DateFormat("yyyy"))
2-element Vector{Date}:
 2015-01-01
 2016-01-01
```

Pour plus de commodité, vous pouvez passer la chaîne de format directement (par exemple, `Date("2015-01-01","y-m-d")`), bien que cette forme entraîne des coûts de performance si vous analysez le même format plusieurs fois, car elle crée en interne un nouvel objet `DateFormat` à chaque fois.

En plus des constructeurs, un `Date` ou `DateTime` peut être construit à partir de chaînes en utilisant les fonctions [`parse`](@ref) et [`tryparse`](@ref), mais avec un troisième argument optionnel de type `DateFormat` spécifiant le format ; par exemple, `parse(Date, "06.23.2013", dateformat"m.d.y")`, ou `tryparse(DateTime, "1999-12-31T23:59:59")` qui utilise le format par défaut. La différence notable entre les fonctions est qu'avec `4d61726b646f776e2e436f64652822222c202274727970617273652229_40726566`, une erreur n'est pas lancée si la chaîne est vide ou dans un format invalide ; à la place, `nothing` est retourné.

!!! compat "Julia 1.9"
    Avant Julia 1.9, des chaînes vides pouvaient être passées aux constructeurs et à `parse` sans erreur, retournant respectivement `DateTime(1)`, `Date(1)` ou `Time(0)`. De même, `tryparse` ne retournait pas `nothing`.


Une suite complète de tests et d'exemples de parsing et de formatage est disponible dans [`stdlib/Dates/test/io.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/io.jl).

## Durations/Comparisons

Trouver la durée entre deux [`Date`](@ref) ou [`DateTime`](@ref) est simple étant donné leur représentation sous-jacente en tant que `UTInstant{Day}` et `UTInstant{Millisecond}`, respectivement. La différence entre `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` est renvoyée en nombre de [`Day`](@ref), et `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` en nombre de [`Millisecond`](@ref). De même, comparer [`TimeType`](@ref) est une simple question de comparaison des instants machine sous-jacents (qui à son tour compare les valeurs internes [`Int64`](@ref)).

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

Parce que les types [`Date`](@ref) et [`DateTime`](@ref) sont stockés en tant que valeurs uniques [`Int64`](@ref), les parties ou champs de date peuvent être récupérés via des fonctions d'accès. Les accesseurs en minuscules renvoient le champ sous forme d'entier :

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

Les méthodes composées sont fournies car il est plus efficace d'accéder à plusieurs champs en même temps plutôt qu'individuellement :

```jldoctest tdate
julia> Dates.yearmonth(t)
(2014, 1)

julia> Dates.monthday(t)
(1, 31)

julia> Dates.yearmonthday(t)
(2014, 1, 31)
```

On peut également accéder à la valeur sous-jacente `UTInstant` ou à la valeur entière :

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

Les fonctions de requête fournissent des informations calendaires sur un [`TimeType`](@ref). Elles incluent des informations sur le jour de la semaine :

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

Mois de l'année :

```jldoctest tdate2
julia> Dates.monthname(t)
"January"

julia> Dates.daysinmonth(t)
31
```

Ainsi que des informations sur l'année et le trimestre de [`TimeType`](@ref) :

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

Les méthodes [`dayname`](@ref) et [`monthname`](@ref) peuvent également prendre un mot-clé `locale` optionnel qui peut être utilisé pour renvoyer le nom du jour ou du mois de l'année pour d'autres langues/locales. Il existe également des versions de ces fonctions renvoyant les noms abrégés, à savoir [`dayabbr`](@ref) et [`monthabbr`](@ref). D'abord, le mappage est chargé dans la variable `LOCALES` :

```jldoctest tdate2
julia> french_months = ["janvier", "février", "mars", "avril", "mai", "juin",
                        "juillet", "août", "septembre", "octobre", "novembre", "décembre"];

julia> french_months_abbrev = ["janv","févr","mars","avril","mai","juin",
                              "juil","août","sept","oct","nov","déc"];

julia> french_days = ["lundi","mardi","mercredi","jeudi","vendredi","samedi","dimanche"];

julia> Dates.LOCALES["french"] = Dates.DateLocale(french_months, french_months_abbrev, french_days, [""]);
```

Les fonctions mentionnées ci-dessus peuvent ensuite être utilisées pour effectuer les requêtes :

```jldoctest tdate2
julia> Dates.dayname(t;locale="french")
"vendredi"

julia> Dates.monthname(t;locale="french")
"janvier"

julia> Dates.monthabbr(t;locale="french")
"janv"
```

Puisque les versions abrégées des jours ne sont pas chargées, essayer d'utiliser la fonction `dayabbr` générera une erreur.

```jldoctest tdate2
julia> Dates.dayabbr(t;locale="french")
ERROR: BoundsError: attempt to access 1-element Vector{String} at index [5]
Stacktrace:
[...]
```

## TimeType-Period Arithmetic

Il est bon de se familiariser avec la façon dont l'arithmétique des périodes de date est gérée lors de l'utilisation de tout langage ou cadre de date, car il y a certains [tricky issues](https://codeblog.jonskeet.uk/2010/12/01/the-joys-of-date-time-arithmetic/) à traiter (bien que beaucoup moins pour les types de précision jour).

Le module `Dates` essaie de suivre le principe simple de changer le moins possible lors de l'exécution de l'arithmétique [`Period`](@ref). Cette approche est également souvent connue sous le nom d'arithmétique *calendrique* ou ce que vous devineriez probablement si quelqu'un vous posait la même question lors d'une conversation. Pourquoi tout ce bruit à ce sujet ? Prenons un exemple classique : ajoutez 1 mois au 31 janvier 2014. Quelle est la réponse ? Javascript dira [March 3](https://markhneedham.com/blog/2009/01/07/javascript-add-a-month-to-a-date/) (suppose 31 jours). PHP dit [March 2](https://stackoverflow.com/questions/5760262/php-adding-months-to-a-date-while-not-exceeding-the-last-day-of-the-month) (suppose 30 jours). Le fait est qu'il n'y a pas de bonne réponse. Dans le module `Dates`, il donne le résultat du 28 février. Comment cela se détermine-t-il ? Considérez le classique jeu de hasard 7-7-7 dans les casinos.

Maintenant, imaginez simplement qu'au lieu de 7-7-7, les emplacements sont Année-Mois-Jour, ou dans notre exemple, 2014-01-31. Lorsque vous demandez à ajouter 1 mois à cette date, l'emplacement du mois est incrémenté, donc maintenant nous avons 2014-02-31. Ensuite, le numéro du jour est vérifié s'il est supérieur au dernier jour valide du nouveau mois ; si c'est le cas (comme dans l'exemple ci-dessus), le numéro du jour est ajusté à la baisse au dernier jour valide (28). Quelles sont les conséquences de cette approche ? Allez-y et ajoutez un autre mois à notre date, `2014-02-28 + Mois(1) == 2014-03-28`. Quoi ? Vous vous attendiez au dernier jour de mars ? Non, désolé, rappelez-vous les emplacements 7-7-7. Aussi peu d'emplacements que possible vont changer, donc nous incrémentons d'abord l'emplacement du mois de 1, 2014-03-28, et boum, nous avons terminé car c'est une date valide. D'autre part, si nous devions ajouter 2 mois à notre date d'origine, 2014-01-31, alors nous nous retrouvons avec 2014-03-31, comme prévu. L'autre conséquence de cette approche est une perte d'associativité lorsque un ordre spécifique est imposé (c'est-à-dire que l'ajout de choses dans des ordres différents donne des résultats différents). Par exemple :

```jldoctest
julia> (Date(2014,1,29)+Dates.Day(1)) + Dates.Month(1)
2014-02-28

julia> (Date(2014,1,29)+Dates.Month(1)) + Dates.Day(1)
2014-03-01
```

Que se passe-t-il là-bas ? Dans la première ligne, nous ajoutons 1 jour au 29 janvier, ce qui donne 2014-01-30 ; puis nous ajoutons 1 mois, donc nous obtenons 2014-02-30, qui est ensuite ajusté à 2014-02-28. Dans le deuxième exemple, nous ajoutons 1 mois *en premier*, ce qui nous donne 2014-02-29, qui est ajusté à 2014-02-28, et *ensuite* nous ajoutons 1 jour, ce qui donne 2014-03-01. Un principe de conception qui aide dans ce cas est que, en présence de plusieurs Périodes, les opérations seront ordonnées par les *types* des Périodes, et non par leur valeur ou leur ordre positionnel ; cela signifie que `Année` sera toujours ajouté en premier, puis `Mois`, puis `Semaine`, etc. Ainsi, ce qui suit *donne* effectivement une associativité et fonctionne parfaitement :

```jldoctest
julia> Date(2014,1,29) + Dates.Day(1) + Dates.Month(1)
2014-03-01

julia> Date(2014,1,29) + Dates.Month(1) + Dates.Day(1)
2014-03-01
```

Difficile ? Peut-être. Que doit faire un utilisateur innocent de `Dates` ? En fin de compte, il faut être conscient que forcer explicitement une certaine associativité, lorsqu'on traite des mois, peut conduire à des résultats inattendus, mais sinon, tout devrait fonctionner comme prévu. Heureusement, c'est à peu près l'étendue des cas étranges dans l'arithmétique des périodes de date lorsqu'on traite du temps en UT (en évitant les "joies" de la gestion de l'heure d'été, des secondes intercalaires, etc.).

En bonus, tous les objets arithmétiques de période fonctionnent directement avec des plages :

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

Aussi pratique que soit l'arithmétique des périodes de dates, souvent les types de calculs nécessaires sur les dates prennent une nature *calendaire* ou *temporelle* plutôt qu'un nombre fixe de périodes. Les jours fériés en sont un parfait exemple ; la plupart suivent des règles telles que "Memorial Day = Dernier lundi de mai", ou "Thanksgiving = 4ème jeudi de novembre". Ces types d'expressions temporelles traitent de règles relatives au calendrier, comme le premier ou le dernier du mois, le mardi prochain, ou les premiers et troisièmes mercredis, etc.

Le module `Dates` fournit l'API *ajusteur* à travers plusieurs méthodes pratiques qui aident à exprimer de manière simple et succincte des règles temporelles. Le premier groupe de méthodes d'ajustement concerne le premier et le dernier des semaines, mois, trimestres et années. Chacune d'elles prend un seul [`TimeType`](@ref) en entrée et retourne ou *ajuste à* le premier ou le dernier de la période souhaitée par rapport à l'entrée.

```jldoctest
julia> Dates.firstdayofweek(Date(2014,7,16)) # Adjusts the input to the Monday of the input's week
2014-07-14

julia> Dates.lastdayofmonth(Date(2014,7,16)) # Adjusts to the last day of the input's month
2014-07-31

julia> Dates.lastdayofquarter(Date(2014,7,16)) # Adjusts to the last day of the input's quarter
2014-09-30
```

Les deux méthodes d'ordre supérieur suivantes, [`tonext`](@ref), et [`toprev`](@ref), généralisent le travail avec des expressions temporelles en prenant un `DateFunction` comme premier argument, ainsi qu'un [`TimeType`](@ref) de départ. Un `DateFunction` est simplement une fonction, généralement anonyme, qui prend un seul `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566` en entrée et retourne un [`Bool`](@ref), `true` indiquant un critère d'ajustement satisfait. Par exemple :

```jldoctest
julia> istuesday = x->Dates.dayofweek(x) == Dates.Tuesday; # Returns true if the day of the week of x is Tuesday

julia> Dates.tonext(istuesday, Date(2014,7,13)) # 2014-07-13 is a Sunday
2014-07-15

julia> Dates.tonext(Date(2014,7,13), Dates.Tuesday) # Convenience method provided for day of the week adjustments
2014-07-15
```

Ceci est utile avec la syntaxe do-block pour des expressions temporelles plus complexes :

```jldoctest
julia> Dates.tonext(Date(2014,7,13)) do x
           # Return true on the 4th Thursday of November (Thanksgiving)
           Dates.dayofweek(x) == Dates.Thursday &&
           Dates.dayofweekofmonth(x) == 4 &&
           Dates.month(x) == Dates.November
       end
2014-11-27
```

La méthode [`Base.filter`](@ref) peut être utilisée pour obtenir toutes les dates/moments valides dans une plage spécifiée :

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

Des exemples et des tests supplémentaires sont disponibles dans [`stdlib/Dates/test/adjusters.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/adjusters.jl).

## Period Types

Les périodes sont une vue humaine de durées de temps discrètes, parfois irrégulières. Considérez 1 mois ; cela pourrait représenter, en jours, une valeur de 28, 29, 30 ou 31 selon le contexte de l'année et du mois. Ou une année pourrait représenter 365 ou 366 jours dans le cas d'une année bissextile. [`Period`](@ref) types sont de simples [`Int64`](@ref) wrappers et sont construits en enveloppant tout type convertible en `Int64`, c'est-à-dire `Year(1)` ou `Month(3.0)`. L'arithmétique entre `4d61726b646f776e2e436f64652822222c2022506572696f642229_40726566` du même type se comporte comme des entiers, et une arithmétique `Période-Réel` limitée est disponible. Vous pouvez extraire l'entier sous-jacent avec [`Dates.value`](@ref).

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

Représenter des périodes ou des durées qui ne sont pas des multiples entiers des types de base peut être réalisé avec le type [`Dates.CompoundPeriod`](@ref). Des périodes composées peuvent être construites manuellement à partir de types simples [`Period`](@ref). De plus, la fonction [`canonicalize`](@ref) peut être utilisée pour décomposer une période en un `4d61726b646f776e2e436f64652822222c202244617465732e436f6d706f756e64506572696f642229_40726566`. Cela est particulièrement utile pour convertir une durée, par exemple, une différence de deux `DateTime`, en une représentation plus pratique.

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

[`Date`](@ref) et [`DateTime`](@ref) peuvent être arrondis à une résolution spécifiée (par exemple, 1 mois ou 15 minutes) avec [`floor`](@ref), [`ceil`](@ref), ou [`round`](@ref) :

```jldoctest
julia> floor(Date(1985, 8, 16), Dates.Month)
1985-08-01

julia> ceil(DateTime(2013, 2, 13, 0, 31, 20), Dates.Minute(15))
2013-02-13T00:45:00

julia> round(DateTime(2016, 8, 6, 20, 15), Dates.Day)
2016-08-07T00:00:00
```

Contrairement à la méthode numérique [`round`](@ref), qui par défaut favorise les nombres pairs en cas d'égalité, la méthode [`TimeType`](@ref)`4d61726b646f776e2e436f64652822222c2022726f756e642229_40726566` utilise le mode d'arrondi `RoundNearestTiesUp`. (Il est difficile de deviner ce que signifierait un arrondi à "l'entier pair le plus proche" `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566`.) Des détails supplémentaires sur les `RoundingMode` disponibles peuvent être trouvés dans le [API reference](@ref stdlib-dates-api).

L'arrondi devrait généralement se comporter comme prévu, mais il existe quelques cas dans lesquels le comportement attendu n'est pas évident.

### Rounding Epoch

Dans de nombreux cas, la résolution spécifiée pour l'arrondi (par exemple, `Dates.Second(30)`) se divise uniformément dans la période suivante la plus grande (dans ce cas, `Dates.Minute(1)`). Mais le comportement d'arrondi dans les cas où cela n'est pas vrai peut prêter à confusion. Quel est le résultat attendu de l'arrondi d'un [`DateTime`](@ref) à l'heure la plus proche de 10 heures ?

```jldoctest
julia> round(DateTime(2016, 7, 17, 11, 55), Dates.Hour(10))
2016-07-17T12:00:00
```

Cela peut sembler déroutant, étant donné que l'heure (12) n'est pas divisible par 10. La raison pour laquelle `2016-07-17T12:00:00` a été choisie est qu'elle est 17 676 660 heures après `0000-01-01T00:00:00`, et 17 676 660 est divisible par 10.

En tant que Julia [`Date`](@ref) et [`DateTime`](@ref), les valeurs sont représentées selon la norme ISO 8601, `0000-01-01T00:00:00` a été choisie comme base (ou "époque d'arrondi") à partir de laquelle commencer le comptage des jours (et des millisecondes) utilisés dans les calculs d'arrondi. (Notez que cela diffère légèrement de la représentation interne de Julia des `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` utilisant [Rata Die notation](https://en.wikipedia.org/wiki/Rata_Die) ; mais puisque la norme ISO 8601 est la plus visible pour l'utilisateur final, `0000-01-01T00:00:00` a été choisie comme époque d'arrondi au lieu de `0000-12-31T00:00:00` utilisée en interne pour minimiser la confusion.)

La seule exception à l'utilisation de `0000-01-01T00:00:00` comme époque d'arrondi est lors de l'arrondi aux semaines. L'arrondi à la semaine la plus proche renverra toujours un lundi (le premier jour de la semaine tel que spécifié par l'ISO 8601). Pour cette raison, nous utilisons `0000-01-03T00:00:00` (le premier jour de la première semaine de l'année 0000, tel que défini par l'ISO 8601) comme base lors de l'arrondi à un nombre de semaines.

Voici un cas connexe dans lequel le comportement attendu n'est pas nécessairement évident : Que se passe-t-il lorsque nous arrondissons au `P(2)` le plus proche, où `P` est un type [`Period`](@ref) ? Dans certains cas (en particulier, lorsque `P <: Dates.TimePeriod`), la réponse est claire :

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Hour(2))
2016-07-17T08:00:00

julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Minute(2))
2016-07-17T08:56:00
```

Cela semble évident, car deux de chacune de ces périodes se divise toujours également dans la période d'ordre supérieure suivante. Mais dans le cas de deux mois (qui se divise toujours également en un an), la réponse peut être surprenante :

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Month(2))
2016-07-01T00:00:00
```

Pourquoi arrondir au premier jour de juillet, même si c'est le mois 7 (un nombre impair) ? La clé est que les mois sont indexés à partir de 1 (le premier mois est assigné 1), contrairement aux heures, minutes, secondes et millisecondes (dont le premier est assigné 0).

Cela signifie que l'arrondi d'un [`DateTime`](@ref) à un multiple pair de secondes, minutes, heures ou années (car la spécification ISO 8601 inclut une année zéro) donnera un `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` avec une valeur paire dans ce champ, tandis que l'arrondi d'un `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` à un multiple pair de mois entraînera un champ mois ayant une valeur impaire. Étant donné que les mois et les années peuvent contenir un nombre irrégulier de jours, il est incertain que l'arrondi à un nombre pair de jours donnera une valeur paire dans le champ des jours.

Voir le [API reference](@ref stdlib-dates-api) pour des informations supplémentaires sur les méthodes exportées du module `Dates`.

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

Les valeurs `Date` et `DateTime` peuvent être arrondies à une résolution spécifiée (par exemple, 1 mois ou 15 minutes) avec `floor`, `ceil` ou `round`.

```@docs
Base.floor(::Dates.TimeType, ::Dates.Period)
Base.ceil(::Dates.TimeType, ::Dates.Period)
Base.round(::Dates.TimeType, ::Dates.Period, ::RoundingMode{:NearestTiesUp})
```

La plupart des valeurs `Period` peuvent également être arrondies à une résolution spécifiée :

```@docs
Base.floor(::Dates.ConvertiblePeriod, ::T) where T <: Dates.ConvertiblePeriod
Base.ceil(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod)
Base.round(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod, ::RoundingMode{:NearestTiesUp})
```

Les fonctions suivantes ne sont pas exportées :

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

Jours de la semaine :

| Variable    | Abbr. | Value (Int) |
|:----------- |:----- |:----------- |
| `Monday`    | `Mon` | 1           |
| `Tuesday`   | `Tue` | 2           |
| `Wednesday` | `Wed` | 3           |
| `Thursday`  | `Thu` | 4           |
| `Friday`    | `Fri` | 5           |
| `Saturday`  | `Sat` | 6           |
| `Sunday`    | `Sun` | 7           |

Mois de l'année :

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
