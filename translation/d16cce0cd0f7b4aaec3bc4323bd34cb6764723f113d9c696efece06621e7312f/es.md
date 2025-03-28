# Dates

```@meta
DocTestSetup = :(using Dates)
```

El módulo `Dates` proporciona dos tipos para trabajar con fechas: [`Date`](@ref) y [`DateTime`](@ref), que representan precisión de días y milisegundos, respectivamente; ambos son subtipos del abstracto [`TimeType`](@ref). La motivación para tener tipos distintos es simple: algunas operaciones son mucho más simples, tanto en términos de código como de razonamiento mental, cuando no se tienen que lidiar con las complejidades de una mayor precisión. Por ejemplo, dado que el tipo `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` solo se resuelve a la precisión de una sola fecha (es decir, sin horas, minutos o segundos), las consideraciones normales para zonas horarias, horario de verano y segundos intercalares son innecesarias y se evitan.

Tanto [`Date`](@ref) como [`DateTime`](@ref) son básicamente envoltorios inmutables [`Int64`](@ref). El único campo `instant` de cualquiera de los tipos es en realidad un tipo `UTInstant{P}`, que representa una línea de tiempo de máquina en continuo aumento basada en el segundo UT [^1]. El tipo `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` no es consciente de las zonas horarias (*naive*, en la jerga de Python), análogo a un *LocalDateTime* en Java 8. Se puede agregar funcionalidad adicional de zona horaria a través de [TimeZones.jl package](https://github.com/JuliaTime/TimeZones.jl/), que compila el [IANA time zone database](https://www.iana.org/time-zones). Tanto `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` como `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` se basan en el estándar [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601), que sigue el calendario gregoriano proleptico. Una nota es que el estándar ISO 8601 es particular sobre las fechas AC/ERA. En general, el último día de la era AC/ERA, 31-12-1 AC/ERA, fue seguido por 1-1-1 DC/CE, por lo que no existe el año cero. Sin embargo, el estándar ISO establece que 1 AC/ERA es el año cero, por lo que `0000-12-31` es el día anterior a `0001-01-01`, y el año `-0001` (sí, menos uno para el año) es 2 AC/ERA, el año `-0002` es 3 AC/ERA, etc.

[^1]: The notion of the UT second is actually quite fundamental. There are basically two different notions of time generally accepted, one based on the physical rotation of the earth (one full rotation = 1 day), the other based on the SI second (a fixed, constant value). These are radically different! Think about it, a "UT second", as defined relative to the rotation of the earth, may have a different absolute length depending on the day! Anyway, the fact that [`Date`](@ref) and [`DateTime`](@ref) are based on UT seconds is a simplifying, yet honest assumption so that things like leap seconds and all their complexity can be avoided. This basis of time is formally called [UT](https://en.wikipedia.org/wiki/Universal_Time) or UT1. Basing types on the UT second basically means that every minute has 60 seconds and every day has 24 hours and leads to more natural calculations when working with calendar dates.

## Constructors

[`Date`](@ref) y [`DateTime`](@ref) tipos pueden ser construidos por tipos enteros o [`Period`](@ref), mediante análisis, o a través de ajustadores (más sobre eso más adelante):

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

[`Date`](@ref) o [`DateTime`](@ref) el análisis se logra mediante el uso de cadenas de formato. Las cadenas de formato funcionan con la noción de definir "espacios" *delimitados* o *de ancho fijo* que contienen un período para analizar y pasar el texto a analizar y la cadena de formato a un `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` o `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` constructor, de la forma `Date("2015-01-01",dateformat"y-m-d")` o `DateTime("20150101",dateformat"yyyymmdd")`.

Los espacios delimitados se marcan especificando el delimitador que el analizador debe esperar entre dos períodos subsiguientes; así que `"y-m-d"` le indica al analizador que entre el primer y el segundo espacio en una cadena de fecha como `"2014-07-16"`, debe encontrar el carácter `-`. Los caracteres `y`, `m` y `d` le indican al analizador qué períodos analizar en cada espacio.

Como en el caso de los constructores anteriores, como `Date(2013)`, los `DateFormat` delimitados permiten partes faltantes de fechas y horas siempre que las partes anteriores estén dadas. Las otras partes reciben los valores predeterminados habituales. Por ejemplo, `Date("1981-03", dateformat"y-m-d")` devuelve `1981-03-01`, mientras que `Date("31/12", dateformat"d/m/y")` da `0001-12-31`. (Tenga en cuenta que el año predeterminado es 1 d.C./E.C.) Sin embargo, una cadena vacía siempre lanza un `ArgumentError`.

Los espacios de ancho fijo se especifican repitiendo el carácter de punto el número de veces correspondiente al ancho sin delimitador entre caracteres. Así que `dateformat"yyyymmdd"` correspondería a una cadena de fecha como `"20140716"`. El analizador distingue un espacio de ancho fijo por la ausencia de un delimitador, notando la transición `"yyyymm"` de un carácter de punto al siguiente.

El soporte para el análisis de meses en formato de texto también se admite a través de los caracteres `u` y `U`, para nombres de meses abreviados y de longitud completa, respectivamente. Por defecto, solo se admiten nombres de meses en inglés, por lo que `u` corresponde a "Ene", "Feb", "Mar", etc. Y `U` corresponde a "Enero", "Febrero", "Marzo", etc. Similar a otras funciones de mapeo nombre=>valor [`dayname`](@ref) y [`monthname`](@ref), se pueden cargar locales personalizadas pasando el mapeo `locale=>Dict{String,Int}` a los diccionarios `MONTHTOVALUEABBR` y `MONTHTOVALUE` para nombres de meses abreviados y de nombre completo, respectivamente.

Los ejemplos anteriores utilizaron el macro de cadena `dateformat""`. Este macro crea un objeto `DateFormat` una vez cuando se expande el macro y utiliza el mismo objeto `DateFormat` incluso si un fragmento de código se ejecuta varias veces.

```jldoctest
julia> for i = 1:10^5
           Date("2015-01-01", dateformat"y-m-d")
       end
```

O puedes crear el objeto DateFormat explícitamente:

```jldoctest
julia> df = DateFormat("y-m-d");

julia> dt = Date("2015-01-01",df)
2015-01-01

julia> dt2 = Date("2015-01-02",df)
2015-01-02
```

Alternativamente, usa la difusión:

```jldoctest
julia> years = ["2015", "2016"];

julia> Date.(years, DateFormat("yyyy"))
2-element Vector{Date}:
 2015-01-01
 2016-01-01
```

Para conveniencia, puedes pasar la cadena de formato directamente (por ejemplo, `Date("2015-01-01","y-m-d")`), aunque esta forma incurre en costos de rendimiento si estás analizando el mismo formato repetidamente, ya que internamente crea un nuevo objeto `DateFormat` cada vez.

Además de los constructores, un `Date` o `DateTime` se puede construir a partir de cadenas utilizando las funciones [`parse`](@ref) y [`tryparse`](@ref), pero con un tercer argumento opcional de tipo `DateFormat` que especifica el formato; por ejemplo, `parse(Date, "06.23.2013", dateformat"m.d.y")`, o `tryparse(DateTime, "1999-12-31T23:59:59")` que utiliza el formato predeterminado. La diferencia notable entre las funciones es que con `4d61726b646f776e2e436f64652822222c202274727970617273652229_40726566`, no se lanza un error si la cadena está vacía o en un formato inválido; en su lugar, se devuelve `nothing`.

!!! compat "Julia 1.9"
    Antes de Julia 1.9, las cadenas vacías podían ser pasadas a constructores y `parse` sin error, devolviendo como corresponde `DateTime(1)`, `Date(1)` o `Time(0)`. Del mismo modo, `tryparse` no devolvía `nothing`.


Un conjunto completo de pruebas y ejemplos de análisis y formato está disponible en [`stdlib/Dates/test/io.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/io.jl).

## Durations/Comparisons

Encontrar la duración entre dos [`Date`](@ref) o [`DateTime`](@ref) es sencillo dado su representación subyacente como `UTInstant{Day}` y `UTInstant{Millisecond}`, respectivamente. La diferencia entre `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` se devuelve en el número de [`Day`](@ref), y `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` en el número de [`Millisecond`](@ref). De manera similar, comparar [`TimeType`](@ref) es un simple asunto de comparar los instantes de máquina subyacentes (que a su vez compara los valores internos [`Int64`](@ref)).

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

Debido a que los tipos [`Date`](@ref) y [`DateTime`](@ref) se almacenan como valores únicos [`Int64`](@ref), las partes o campos de la fecha se pueden recuperar a través de funciones de acceso. Los accesores en minúsculas devuelven el campo como un entero:

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

Se proporcionan métodos compuestos porque es más eficiente acceder a múltiples campos al mismo tiempo que de forma individual:

```jldoctest tdate
julia> Dates.yearmonth(t)
(2014, 1)

julia> Dates.monthday(t)
(1, 31)

julia> Dates.yearmonthday(t)
(2014, 1, 31)
```

También se puede acceder al `UTInstant` subyacente o al valor entero:

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

Las funciones de consulta proporcionan información calendárica sobre un [`TimeType`](@ref). Incluyen información sobre el día de la semana:

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

Mes del año:

```jldoctest tdate2
julia> Dates.monthname(t)
"January"

julia> Dates.daysinmonth(t)
31
```

Así como información sobre el año y el trimestre de [`TimeType`](@ref):

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

Los métodos [`dayname`](@ref) y [`monthname`](@ref) también pueden tomar una palabra clave opcional `locale` que se puede usar para devolver el nombre del día o del mes del año para otros idiomas/locales. También hay versiones de estas funciones que devuelven los nombres abreviados, a saber, [`dayabbr`](@ref) y [`monthabbr`](@ref). Primero, el mapeo se carga en la variable `LOCALES`:

```jldoctest tdate2
julia> french_months = ["janvier", "février", "mars", "avril", "mai", "juin",
                        "juillet", "août", "septembre", "octobre", "novembre", "décembre"];

julia> french_months_abbrev = ["janv","févr","mars","avril","mai","juin",
                              "juil","août","sept","oct","nov","déc"];

julia> french_days = ["lundi","mardi","mercredi","jeudi","vendredi","samedi","dimanche"];

julia> Dates.LOCALES["french"] = Dates.DateLocale(french_months, french_months_abbrev, french_days, [""]);
```

Las funciones mencionadas anteriormente se pueden utilizar para realizar las consultas:

```jldoctest tdate2
julia> Dates.dayname(t;locale="french")
"vendredi"

julia> Dates.monthname(t;locale="french")
"janvier"

julia> Dates.monthabbr(t;locale="french")
"janv"
```

Dado que las versiones abreviadas de los días no están cargadas, intentar usar la función `dayabbr` generará un error.

```jldoctest tdate2
julia> Dates.dayabbr(t;locale="french")
ERROR: BoundsError: attempt to access 1-element Vector{String} at index [5]
Stacktrace:
[...]
```

## TimeType-Period Arithmetic

Es una buena práctica, al usar cualquier lenguaje/framework de fechas, estar familiarizado con cómo se maneja la aritmética de períodos de fechas, ya que hay algunos [tricky issues](https://codeblog.jonskeet.uk/2010/12/01/the-joys-of-date-time-arithmetic/) con los que lidiar (aunque mucho menos para tipos de precisión diaria).

El enfoque del módulo `Dates` intenta seguir el simple principio de cambiar lo menos posible al realizar la aritmética [`Period`](@ref). Este enfoque también se conoce a menudo como aritmética *calendárica* o lo que probablemente adivinarías si alguien te preguntara la misma operación en una conversación. ¿Por qué tanto alboroto sobre esto? Tomemos un ejemplo clásico: añade 1 mes al 31 de enero de 2014. ¿Cuál es la respuesta? Javascript dirá [March 3](https://markhneedham.com/blog/2009/01/07/javascript-add-a-month-to-a-date/) (asume 31 días). PHP dice [March 2](https://stackoverflow.com/questions/5760262/php-adding-months-to-a-date-while-not-exceeding-the-last-day-of-the-month) (asume 30 días). El hecho es que no hay una respuesta correcta. En el módulo `Dates`, da como resultado el 28 de febrero. ¿Cómo lo determina? Considera el clásico juego de apuestas 7-7-7 en los casinos.

Ahora solo imagina que en lugar de 7-7-7, las ranuras son Año-Mes-Día, o en nuestro ejemplo, 2014-01-31. Cuando pides agregar 1 mes a esta fecha, la ranura del mes se incrementa, así que ahora tenemos 2014-02-31. Luego se verifica si el número del día es mayor que el último día válido del nuevo mes; si lo es (como en el caso anterior), el número del día se ajusta hacia abajo al último día válido (28). ¿Cuáles son las ramificaciones de este enfoque? Adelante, agrega otro mes a nuestra fecha, `2014-02-28 + Month(1) == 2014-03-28`. ¿Qué? ¿Esperabas el último día de marzo? No, lo siento, recuerda las ranuras 7-7-7. Se van a cambiar la menor cantidad de ranuras posible, así que primero incrementamos la ranura del mes en 1, 2014-03-28, y listo, hemos terminado porque es una fecha válida. Por otro lado, si tuviéramos que agregar 2 meses a nuestra fecha original, 2014-01-31, entonces terminamos con 2014-03-31, como se esperaba. La otra ramificación de este enfoque es una pérdida de asociatividad cuando se fuerza un orden específico (es decir, agregar cosas en diferentes órdenes resulta en diferentes resultados). Por ejemplo:

```jldoctest
julia> (Date(2014,1,29)+Dates.Day(1)) + Dates.Month(1)
2014-02-28

julia> (Date(2014,1,29)+Dates.Month(1)) + Dates.Day(1)
2014-03-01
```

¿Qué está pasando allí? En la primera línea, estamos sumando 1 día al 29 de enero, lo que resulta en 2014-01-30; luego añadimos 1 mes, así que obtenemos 2014-02-30, que luego se ajusta a 2014-02-28. En el segundo ejemplo, primero añadimos 1 mes, donde obtenemos 2014-02-29, que se ajusta a 2014-02-28, y *luego* añadimos 1 día, lo que resulta en 2014-03-01. Un principio de diseño que ayuda en este caso es que, en presencia de múltiples Períodos, las operaciones se ordenarán por los *tipos* de los Períodos, no por su valor o orden posicional; esto significa que `Año` siempre se añadirá primero, luego `Mes`, luego `Semana`, etc. Por lo tanto, lo siguiente *sí* resulta en asociatividad y funciona perfectamente:

```jldoctest
julia> Date(2014,1,29) + Dates.Day(1) + Dates.Month(1)
2014-03-01

julia> Date(2014,1,29) + Dates.Month(1) + Dates.Day(1)
2014-03-01
```

¿Complicado? Quizás. ¿Qué debe hacer un usuario inocente de `Dates`? La conclusión es estar consciente de que forzar explícitamente una cierta asociatividad, al tratar con meses, puede llevar a algunos resultados inesperados, pero de lo contrario, todo debería funcionar como se espera. Afortunadamente, esa es prácticamente la extensión de los casos extraños en la aritmética de períodos de fecha al tratar con el tiempo en UT (evitando las "alegrías" de lidiar con el horario de verano, segundos intercalares, etc.).

Como bonificación, todos los objetos de aritmética de períodos funcionan directamente con rangos:

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

Tan conveniente como es la aritmética de períodos de fechas, a menudo los tipos de cálculos necesarios sobre fechas adquieren una naturaleza *calendárica* o *temporal* en lugar de un número fijo de períodos. Los días festivos son un ejemplo perfecto; la mayoría sigue reglas como "Día de los Caídos = Último lunes de mayo", o "Acción de Gracias = 4º jueves de noviembre". Este tipo de expresiones temporales tratan con reglas relativas al calendario, como el primero o el último del mes, el próximo martes, o los primeros y terceros miércoles, etc.

El módulo `Dates` proporciona la API de *ajustador* a través de varios métodos convenientes que ayudan a expresar de manera simple y sucinta las reglas temporales. El primer grupo de métodos de ajustador se ocupa del primero y el último de semanas, meses, trimestres y años. Cada uno toma un único [`TimeType`](@ref) como entrada y devuelve o *ajusta a* el primero o el último del período deseado en relación con la entrada.

```jldoctest
julia> Dates.firstdayofweek(Date(2014,7,16)) # Adjusts the input to the Monday of the input's week
2014-07-14

julia> Dates.lastdayofmonth(Date(2014,7,16)) # Adjusts to the last day of the input's month
2014-07-31

julia> Dates.lastdayofquarter(Date(2014,7,16)) # Adjusts to the last day of the input's quarter
2014-09-30
```

Los siguientes dos métodos de orden superior, [`tonext`](@ref), y [`toprev`](@ref), generalizan el trabajo con expresiones temporales al tomar un `DateFunction` como primer argumento, junto con un [`TimeType`](@ref) inicial. Un `DateFunction` es simplemente una función, generalmente anónima, que toma un solo `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566` como entrada y devuelve un [`Bool`](@ref), `true` indicando un criterio de ajuste satisfecho. Por ejemplo:

```jldoctest
julia> istuesday = x->Dates.dayofweek(x) == Dates.Tuesday; # Returns true if the day of the week of x is Tuesday

julia> Dates.tonext(istuesday, Date(2014,7,13)) # 2014-07-13 is a Sunday
2014-07-15

julia> Dates.tonext(Date(2014,7,13), Dates.Tuesday) # Convenience method provided for day of the week adjustments
2014-07-15
```

Esto es útil con la sintaxis de bloque do para expresiones temporales más complejas:

```jldoctest
julia> Dates.tonext(Date(2014,7,13)) do x
           # Return true on the 4th Thursday of November (Thanksgiving)
           Dates.dayofweek(x) == Dates.Thursday &&
           Dates.dayofweekofmonth(x) == 4 &&
           Dates.month(x) == Dates.November
       end
2014-11-27
```

El método [`Base.filter`](@ref) se puede utilizar para obtener todas las fechas/momentos válidos en un rango especificado:

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

Ejemplos y pruebas adicionales están disponibles en [`stdlib/Dates/test/adjusters.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/adjusters.jl).

## Period Types

Los períodos son una visión humana de duraciones de tiempo discretas, a veces irregulares. Considera 1 mes; podría representar, en días, un valor de 28, 29, 30 o 31 dependiendo del contexto del año y del mes. O un año podría representar 365 o 366 días en el caso de un año bisiesto. [`Period`](@ref) tipos son simples [`Int64`](@ref) envoltorios y se construyen envolviendo cualquier tipo convertible a `Int64`, es decir, `Year(1)` o `Month(3.0)`. La aritmética entre `4d61726b646f776e2e436f64652822222c2022506572696f642229_40726566` del mismo tipo se comporta como enteros, y hay disponible una aritmética limitada `Period-Real`. Puedes extraer el entero subyacente con [`Dates.value`](@ref).

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

Representar períodos o duraciones que no son múltiplos enteros de los tipos básicos se puede lograr con el tipo [`Dates.CompoundPeriod`](@ref). Los períodos compuestos pueden ser construidos manualmente a partir de tipos simples [`Period`](@ref). Además, la función [`canonicalize`](@ref) se puede utilizar para descomponer un período en un `4d61726b646f776e2e436f64652822222c202244617465732e436f6d706f756e64506572696f642229_40726566`. Esto es particularmente útil para convertir una duración, por ejemplo, una diferencia de dos `DateTime`, en una representación más conveniente.

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

[`Date`](@ref) y [`DateTime`](@ref) pueden ser redondeados a una resolución especificada (por ejemplo, 1 mes o 15 minutos) con [`floor`](@ref), [`ceil`](@ref), o [`round`](@ref):

```jldoctest
julia> floor(Date(1985, 8, 16), Dates.Month)
1985-08-01

julia> ceil(DateTime(2013, 2, 13, 0, 31, 20), Dates.Minute(15))
2013-02-13T00:45:00

julia> round(DateTime(2016, 8, 6, 20, 15), Dates.Day)
2016-08-07T00:00:00
```

A diferencia del método numérico [`round`](@ref), que rompe empates hacia el número par por defecto, el método [`TimeType`](@ref)`4d61726b646f776e2e436f64652822222c2022726f756e642229_40726566` utiliza el modo de redondeo `RoundNearestTiesUp`. (Es difícil adivinar qué implicaría romper empates hacia el "par" `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566`.) Se pueden encontrar más detalles sobre los `RoundingMode` disponibles en el [API reference](@ref stdlib-dates-api).

El redondeo debería comportarse generalmente como se espera, pero hay algunos casos en los que el comportamiento esperado no es obvio.

### Rounding Epoch

En muchos casos, la resolución especificada para el redondeo (por ejemplo, `Dates.Second(30)`) se divide uniformemente en el siguiente período más grande (en este caso, `Dates.Minute(1)`). Pero el comportamiento de redondeo en casos en los que esto no es cierto puede llevar a confusión. ¿Cuál es el resultado esperado de redondear un [`DateTime`](@ref) a la hora más cercana de 10 horas?

```jldoctest
julia> round(DateTime(2016, 7, 17, 11, 55), Dates.Hour(10))
2016-07-17T12:00:00
```

Eso puede parecer confuso, dado que la hora (12) no es divisible por 10. La razón por la que se eligió `2016-07-17T12:00:00` es que es 17,676,660 horas después de `0000-01-01T00:00:00`, y 17,676,660 es divisible por 10.

Como los valores de Julia [`Date`](@ref) y [`DateTime`](@ref) se representan de acuerdo con el estándar ISO 8601, se eligió `0000-01-01T00:00:00` como base (o "época de redondeo") desde la cual comenzar el conteo de días (y milisegundos) utilizados en los cálculos de redondeo. (Nota que esto difiere ligeramente de la representación interna de Julia de `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` usando [Rata Die notation](https://en.wikipedia.org/wiki/Rata_Die); pero dado que el estándar ISO 8601 es más visible para el usuario final, se eligió `0000-01-01T00:00:00` como la época de redondeo en lugar de `0000-12-31T00:00:00` utilizada internamente para minimizar la confusión.)

La única excepción al uso de `0000-01-01T00:00:00` como la época de redondeo es al redondear a semanas. Redondear a la semana más cercana siempre devolverá un lunes (el primer día de la semana según lo especificado por la ISO 8601). Por esta razón, usamos `0000-01-03T00:00:00` (el primer día de la primera semana del año 0000, según lo definido por la ISO 8601) como base al redondear a un número de semanas.

Aquí hay un caso relacionado en el que el comportamiento esperado no es necesariamente obvio: ¿Qué sucede cuando redondeamos al más cercano `P(2)`, donde `P` es un tipo [`Period`](@ref)? En algunos casos (específicamente, cuando `P <: Dates.TimePeriod`) la respuesta es clara:

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Hour(2))
2016-07-17T08:00:00

julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Minute(2))
2016-07-17T08:56:00
```

Esto parece obvio, porque dos de cada uno de estos períodos aún se divide uniformemente en el siguiente período de orden mayor. Pero en el caso de dos meses (que aún se divide uniformemente en un año), la respuesta puede ser sorprendente:

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Month(2))
2016-07-01T00:00:00
```

¿Por qué redondear al primer día de julio, aunque sea el mes 7 (un número impar)? La clave es que los meses están indexados desde 1 (el primer mes se asigna el 1), a diferencia de las horas, minutos, segundos y milisegundos (el primero de los cuales se asigna el 0).

Esto significa que redondear un [`DateTime`](@ref) a un múltiplo par de segundos, minutos, horas o años (porque la especificación ISO 8601 incluye un año cero) resultará en un `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` con un valor par en ese campo, mientras que redondear un `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` a un múltiplo par de meses resultará en que el campo de meses tenga un valor impar. Dado que tanto los meses como los años pueden contener un número irregular de días, no está claro si redondear a un número par de días resultará en un valor par en el campo de días.

Consulta el [API reference](@ref stdlib-dates-api) para obtener información adicional sobre los métodos exportados del módulo `Dates`.

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

Los valores de `Date` y `DateTime` se pueden redondear a una resolución especificada (por ejemplo, 1 mes o 15 minutos) con `floor`, `ceil` o `round`.

```@docs
Base.floor(::Dates.TimeType, ::Dates.Period)
Base.ceil(::Dates.TimeType, ::Dates.Period)
Base.round(::Dates.TimeType, ::Dates.Period, ::RoundingMode{:NearestTiesUp})
```

La mayoría de los valores de `Period` también se pueden redondear a una resolución especificada:

```@docs
Base.floor(::Dates.ConvertiblePeriod, ::T) where T <: Dates.ConvertiblePeriod
Base.ceil(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod)
Base.round(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod, ::RoundingMode{:NearestTiesUp})
```

Las siguientes funciones no están exportadas:

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

Días de la Semana:

| Variable    | Abbr. | Value (Int) |
|:----------- |:----- |:----------- |
| `Monday`    | `Mon` | 1           |
| `Tuesday`   | `Tue` | 2           |
| `Wednesday` | `Wed` | 3           |
| `Thursday`  | `Thu` | 4           |
| `Friday`    | `Fri` | 5           |
| `Saturday`  | `Sat` | 6           |
| `Sunday`    | `Sun` | 7           |

Meses del Año:

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
