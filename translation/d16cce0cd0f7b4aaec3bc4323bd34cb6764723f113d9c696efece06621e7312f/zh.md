# Dates

```@meta
DocTestSetup = :(using Dates)
```

`Dates` 模块提供了两种用于处理日期的类型：[`Date`](@ref) 和 [`DateTime`](@ref)，分别表示天和毫秒精度；这两者都是抽象类型 [`TimeType`](@ref) 的子类型。使用不同类型的动机很简单：某些操作在代码和思维推理方面要简单得多，当不必处理更高精度的复杂性时。例如，由于 `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` 类型仅解析为单个日期的精度（即没有小时、分钟或秒），因此时间区、夏令时和闰秒的正常考虑是多余的，可以避免。

[`Date`](@ref) 和 [`DateTime`](@ref) 基本上是不可变的 [`Int64`](@ref) 包装器。任一类型的单个 `instant` 字段实际上是 `UTInstant{P}` 类型，表示基于 UT 秒的持续增加的机器时间线 [^1]。`4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` 类型并不考虑时区（在 Python 术语中称为 *naive*），类似于 Java 8 中的 *LocalDateTime*。可以通过 [TimeZones.jl package](https://github.com/JuliaTime/TimeZones.jl/) 添加额外的时区功能，该功能编译 [IANA time zone database](https://www.iana.org/time-zones)。`4d61726b646f776e2e436f64652822222c2022446174652229_40726566` 和 `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` 都基于 [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) 标准，该标准遵循前瞻性公历。需要注意的是，ISO 8601 标准对公元前/公元前日期有特别规定。一般来说，公元前/公元前时代的最后一天，公元前 1 年 12 月 31 日，之后是公元 1 年 1 月 1 日，因此不存在零年。然而，ISO 标准规定公元前 1 年是零年，因此 `0000-12-31` 是 `0001-01-01` 之前的一天，而年份 `-0001`（是的，负一的年份）是公元前 2 年，年份 `-0002` 是公元前 3 年，依此类推。

[^1]: The notion of the UT second is actually quite fundamental. There are basically two different notions of time generally accepted, one based on the physical rotation of the earth (one full rotation = 1 day), the other based on the SI second (a fixed, constant value). These are radically different! Think about it, a "UT second", as defined relative to the rotation of the earth, may have a different absolute length depending on the day! Anyway, the fact that [`Date`](@ref) and [`DateTime`](@ref) are based on UT seconds is a simplifying, yet honest assumption so that things like leap seconds and all their complexity can be avoided. This basis of time is formally called [UT](https://en.wikipedia.org/wiki/Universal_Time) or UT1. Basing types on the UT second basically means that every minute has 60 seconds and every day has 24 hours and leads to more natural calculations when working with calendar dates.

## Constructors

[`Date`](@ref) 和 [`DateTime`](@ref) 类型可以通过整数或 [`Period`](@ref) 类型构建，通过解析或通过调整器（稍后会详细介绍）:

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

[`Date`](@ref) 或 [`DateTime`](@ref) 的解析是通过使用格式字符串来完成的。格式字符串的工作原理是定义 *分隔* 或 *固定宽度* 的“插槽”，这些插槽包含一个句点以进行解析，并将要解析的文本和格式字符串传递给 `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` 或 `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` 构造函数，形式为 `Date("2015-01-01",dateformat"y-m-d")` 或 `DateTime("20150101",dateformat"yyyymmdd")`。

分隔槽通过指定解析器在两个后续时间段之间应该期待的分隔符来标记；因此，`"y-m-d"` 让解析器知道在像 `"2014-07-16"` 这样的日期字符串中的第一个和第二个槽之间，它应该找到 `-` 字符。`y`、`m` 和 `d` 字符让解析器知道在每个槽中应该解析哪些时间段。

如上面构造函数 `Date(2013)` 的情况，带分隔符的 `DateFormat` 允许日期和时间的某些部分缺失，只要前面的部分给出。其他部分将使用通常的默认值。例如，`Date("1981-03", dateformat"y-m-d")` 返回 `1981-03-01`，而 `Date("31/12", dateformat"d/m/y")` 返回 `0001-12-31`。（请注意，默认年份是公元1年/公历1年。）然而，空字符串始终会抛出 `ArgumentError`。

固定宽度的插槽通过重复句点字符来指定，重复的次数与宽度相对应，字符之间没有分隔符。因此，`dateformat"yyyymmdd"` 将对应于像 `"20140716"` 这样的日期字符串。解析器通过缺少分隔符来区分固定宽度的插槽，注意到从一个句点字符到下一个句点字符的过渡 `"yyyymm"`。

对文本形式的月份解析也通过 `u` 和 `U` 字符支持，分别用于缩写和全名的月份名称。默认情况下，仅支持英语月份名称，因此 `u` 对应于 "Jan"、"Feb"、"Mar" 等。而 `U` 对应于 "January"、"February"、"March" 等。与其他名称=>值映射函数类似，[`dayname`](@ref) 和 [`monthname`](@ref)，可以通过将 `locale=>Dict{String,Int}` 映射传递给 `MONTHTOVALUEABBR` 和 `MONTHTOVALUE` 字典来加载自定义区域设置，分别用于缩写和全名的月份名称。

上述示例使用了 `dateformat""` 字符串宏。该宏在宏展开时创建一个 `DateFormat` 对象，并在多次运行代码片段时使用相同的 `DateFormat` 对象。

```jldoctest
julia> for i = 1:10^5
           Date("2015-01-01", dateformat"y-m-d")
       end
```

或者您可以显式创建 DateFormat 对象：

```jldoctest
julia> df = DateFormat("y-m-d");

julia> dt = Date("2015-01-01",df)
2015-01-01

julia> dt2 = Date("2015-01-02",df)
2015-01-02
```

或者，使用广播：

```jldoctest
julia> years = ["2015", "2016"];

julia> Date.(years, DateFormat("yyyy"))
2-element Vector{Date}:
 2015-01-01
 2016-01-01
```

为了方便，您可以直接传递格式字符串（例如，`Date("2015-01-01","y-m-d")`），尽管这种形式在重复解析相同格式时会产生性能开销，因为它每次都会内部创建一个新的 `DateFormat` 对象。

除了通过构造函数，`Date` 或 `DateTime` 还可以通过字符串构造，使用 [`parse`](@ref) 和 [`tryparse`](@ref) 函数，但可以选择性地传入一个类型为 `DateFormat` 的第三个参数来指定格式；例如，`parse(Date, "06.23.2013", dateformat"m.d.y")`，或 `tryparse(DateTime, "1999-12-31T23:59:59")`，后者使用默认格式。这两个函数之间的显著区别在于，使用 `4d61726b646f776e2e436f64652822222c202274727970617273652229_40726566` 时，如果字符串为空或格式无效，则不会抛出错误；相反，返回 `nothing`。

!!! compat "Julia 1.9"
    在 Julia 1.9 之前，空字符串可以传递给构造函数和 `parse` 而不会出错，返回相应的 `DateTime(1)`、`Date(1)` 或 `Time(0)`。同样，`tryparse` 不会返回 `nothing`。


一整套解析和格式化测试及示例可在 [`stdlib/Dates/test/io.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/io.jl) 中找到。

## Durations/Comparisons

Finding the length of time between two [`Date`](@ref) or [`DateTime`](@ref) is straightforward given their underlying representation as `UTInstant{Day}` and `UTInstant{Millisecond}`, respectively. The difference between [`Date`](@ref) is returned in the number of [`Day`](@ref), and [`DateTime`](@ref) in the number of [`Millisecond`](@ref). Similarly, comparing [`TimeType`](@ref) is a simple matter of comparing the underlying machine instants (which in turn compares the internal [`Int64`](@ref) values).

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

因为 [`Date`](@ref) 和 [`DateTime`](@ref) 类型被存储为单个 [`Int64`](@ref) 值，因此可以通过访问器函数检索日期部分或字段。小写访问器将字段作为整数返回：

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

复合方法的提供是因为同时访问多个字段比单独访问更高效：

```jldoctest tdate
julia> Dates.yearmonth(t)
(2014, 1)

julia> Dates.monthday(t)
(1, 31)

julia> Dates.yearmonthday(t)
(2014, 1, 31)
```

您还可以访问底层的 `UTInstant` 或整数值：

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

查询函数提供有关 [`TimeType`](@ref) 的日历信息。它们包括有关星期几的信息：

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

一年中的月份：

```jldoctest tdate2
julia> Dates.monthname(t)
"January"

julia> Dates.daysinmonth(t)
31
```

关于 [`TimeType`](@ref) 的年份和季度的信息：

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

[`dayname`](@ref) 和 [`monthname`](@ref) 方法还可以接受一个可选的 `locale` 关键字，用于返回其他语言/地区的星期几或月份名称。这些函数还有返回缩写名称的版本，即 [`dayabbr`](@ref) 和 [`monthabbr`](@ref)。首先，映射被加载到 `LOCALES` 变量中：

```jldoctest tdate2
julia> french_months = ["janvier", "février", "mars", "avril", "mai", "juin",
                        "juillet", "août", "septembre", "octobre", "novembre", "décembre"];

julia> french_months_abbrev = ["janv","févr","mars","avril","mai","juin",
                              "juil","août","sept","oct","nov","déc"];

julia> french_days = ["lundi","mardi","mercredi","jeudi","vendredi","samedi","dimanche"];

julia> Dates.LOCALES["french"] = Dates.DateLocale(french_months, french_months_abbrev, french_days, [""]);
```

上述提到的函数可以用来执行查询：

```jldoctest tdate2
julia> Dates.dayname(t;locale="french")
"vendredi"

julia> Dates.monthname(t;locale="french")
"janvier"

julia> Dates.monthabbr(t;locale="french")
"janv"
```

由于未加载日期的缩写版本，尝试使用函数 `dayabbr` 将会抛出错误。

```jldoctest tdate2
julia> Dates.dayabbr(t;locale="french")
ERROR: BoundsError: attempt to access 1-element Vector{String} at index [5]
Stacktrace:
[...]
```

## TimeType-Period Arithmetic

在使用任何语言/日期框架时，熟悉日期周期算术的处理方式是一个好习惯，因为有一些 [tricky issues](https://codeblog.jonskeet.uk/2010/12/01/the-joys-of-date-time-arithmetic/) 需要处理（尽管对于日精度类型来说要少得多）。

`Dates` 模块的方法试图遵循一个简单的原则，即在进行 [`Period`](@ref) 算术运算时尽量减少更改。这种方法通常也被称为 *历法* 算术，或者如果有人在对话中问你同样的计算，你可能会猜到的内容。为什么对此如此关注？让我们来看一个经典的例子：在2014年1月31日加1个月，答案是什么？Javascript 会说 [March 3](https://markhneedham.com/blog/2009/01/07/javascript-add-a-month-to-a-date/)（假设31天）。PHP 说 [March 2](https://stackoverflow.com/questions/5760262/php-adding-months-to-a-date-while-not-exceeding-the-last-day-of-the-month)（假设30天）。事实上，没有正确的答案。在 `Dates` 模块中，它给出的结果是2月28日。它是如何得出这个结果的？考虑一下赌场中的经典7-7-7赌博游戏。

现在想象一下，老虎机的格式不是7-7-7，而是年-月-日，或者在我们的例子中是2014-01-31。当你要求将这个日期加1个月时，月份的槽位会增加，所以现在我们有2014-02-31。然后检查日期数字是否大于新月份的最后有效日期；如果是（如上例所示），日期数字会调整到最后有效日期（28）。这种方法有什么影响呢？继续将我们的日期加一个月，`2014-02-28 + Month(1) == 2014-03-28`。什么？你期待三月的最后一天吗？不，抱歉，记住7-7-7的槽位。尽可能少的槽位会改变，所以我们首先将月份槽位加1，变成2014-03-28，完成，因为这是一个有效的日期。另一方面，如果我们将原始日期2014-01-31加2个月，那么我们最终得到2014-03-31，正如预期的那样。这种方法的另一个影响是，当强制特定顺序时，关联性会丧失（即以不同顺序添加的结果不同）。例如：

```jldoctest
julia> (Date(2014,1,29)+Dates.Day(1)) + Dates.Month(1)
2014-02-28

julia> (Date(2014,1,29)+Dates.Month(1)) + Dates.Day(1)
2014-03-01
```

发生了什么？在第一行中，我们将1天添加到1月29日，这样得到2014-01-30；然后我们添加1个月，所以得到2014-02-30，随后调整为2014-02-28。在第二个例子中，我们*首先*添加1个月，得到2014-02-29，随后调整为2014-02-28，然后*再*添加1天，结果是2014-03-01。一个在这种情况下有帮助的设计原则是，在存在多个周期的情况下，操作将按周期的*类型*排序，而不是它们的值或位置顺序；这意味着`Year`将始终首先添加，然后是`Month`，然后是`Week`，等等。因此，以下*确实*结果是结合性并且正常工作：

```jldoctest
julia> Date(2014,1,29) + Dates.Day(1) + Dates.Month(1)
2014-03-01

julia> Date(2014,1,29) + Dates.Month(1) + Dates.Day(1)
2014-03-01
```

棘手吗？也许吧。一个无辜的 `Dates` 用户该怎么办？底线是要意识到，在处理月份时，明确强制某种结合性可能会导致一些意想不到的结果，但除此之外，一切应该按预期工作。值得庆幸的是，这几乎就是在处理 UT 时间的日期周期算术时奇怪情况的全部（避免处理夏令时、闰秒等的“乐趣”）。

作为额外奖励，所有周期算术对象都可以直接与范围一起使用：

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

尽管日期周期算术非常方便，但通常对日期的计算需要采用*日历*或*时间*的性质，而不是固定的周期数。假期就是一个完美的例子；大多数假期遵循诸如“阵亡将士纪念日 = 五月的最后一个星期一”或“感恩节 = 十一月的第四个星期四”等规则。这些时间表达式处理与日历相关的规则，例如每月的第一天或最后一天，下一个星期二，或第一和第三个星期三等。

`Dates` 模块通过几个方便的方法提供了 *调整器* API，这些方法有助于简单明了地表达时间规则。第一组调整器方法处理周、月、季度和年的首尾。它们每个都接受一个单一的 [`TimeType`](@ref) 作为输入，并返回或 *调整到* 相对于输入的所需周期的首尾。

```jldoctest
julia> Dates.firstdayofweek(Date(2014,7,16)) # Adjusts the input to the Monday of the input's week
2014-07-14

julia> Dates.lastdayofmonth(Date(2014,7,16)) # Adjusts to the last day of the input's month
2014-07-31

julia> Dates.lastdayofquarter(Date(2014,7,16)) # Adjusts to the last day of the input's quarter
2014-09-30
```

下两个高阶方法，[`tonext`](@ref) 和 [`toprev`](@ref)，通过将 `DateFunction` 作为第一个参数，以及一个起始的 [`TimeType`](@ref)，来推广处理时间表达式。`DateFunction` 只是一个函数，通常是匿名的，它接受一个单一的 `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566` 作为输入，并返回一个 [`Bool`](@ref)，`true` 表示满足调整标准。例如：

```jldoctest
julia> istuesday = x->Dates.dayofweek(x) == Dates.Tuesday; # Returns true if the day of the week of x is Tuesday

julia> Dates.tonext(istuesday, Date(2014,7,13)) # 2014-07-13 is a Sunday
2014-07-15

julia> Dates.tonext(Date(2014,7,13), Dates.Tuesday) # Convenience method provided for day of the week adjustments
2014-07-15
```

这在使用 do-block 语法处理更复杂的时间表达式时非常有用：

```jldoctest
julia> Dates.tonext(Date(2014,7,13)) do x
           # Return true on the 4th Thursday of November (Thanksgiving)
           Dates.dayofweek(x) == Dates.Thursday &&
           Dates.dayofweekofmonth(x) == 4 &&
           Dates.month(x) == Dates.November
       end
2014-11-27
```

[`Base.filter`](@ref) 方法可以用来获取指定范围内的所有有效日期/时刻：

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

附加示例和测试可在 [`stdlib/Dates/test/adjusters.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/adjusters.jl) 中获取。

## Period Types

周期是人类对离散的、有时不规则的时间段的看法。考虑1个月；根据年份和月份的上下文，它可以在天数上表示为28、29、30或31。或者在闰年的情况下，一年可以表示为365或366天。 [`Period`](@ref) 类型是简单的 [`Int64`](@ref) 包装器，通过包装任何可转换为 `Int64` 的类型构造，例如 `Year(1)` 或 `Month(3.0)`。同类型的 `4d61726b646f776e2e436f64652822222c2022506572696f642229_40726566` 之间的算术运算表现得像整数，并且有限的 `Period-Real` 算术运算是可用的。您可以使用 [`Dates.value`](@ref) 提取底层整数。

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

表示非整数倍基本类型的周期或持续时间可以通过 [`Dates.CompoundPeriod`](@ref) 类型来实现。复合周期可以通过简单的 [`Period`](@ref) 类型手动构建。此外，[`canonicalize`](@ref) 函数可以用来将一个周期分解为 `4d61726b646f776e2e436f64652822222c202244617465732e436f6d706f756e64506572696f642229_40726566`。这在将持续时间（例如，两个 `DateTime` 的差异）转换为更方便的表示时特别有用。

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

[`Date`](@ref) 和 [`DateTime`](@ref) 的值可以根据指定的分辨率（例如，1 个月或 15 分钟）进行四舍五入，使用 [`floor`](@ref)、[`ceil`](@ref) 或 [`round`](@ref)：

```jldoctest
julia> floor(Date(1985, 8, 16), Dates.Month)
1985-08-01

julia> ceil(DateTime(2013, 2, 13, 0, 31, 20), Dates.Minute(15))
2013-02-13T00:45:00

julia> round(DateTime(2016, 8, 6, 20, 15), Dates.Day)
2016-08-07T00:00:00
```

与默认情况下向偶数倾斜的数字 [`round`](@ref) 方法不同，[`TimeType`](@ref)`4d61726b646f776e2e436f64652822222c2022726f756e642229_40726566` 方法使用 `RoundNearestTiesUp` 舍入模式。（很难猜测向最近的“偶数” `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566` 的舍入会涉及什么。）有关可用 `RoundingMode` 的更多详细信息，请参见 [API reference](@ref stdlib-dates-api)。

四舍五入通常应该按预期进行，但有一些情况下，预期的行为并不明显。

### Rounding Epoch

在许多情况下，指定的舍入分辨率（例如，`Dates.Second(30)`）可以均匀地划分到下一个较大的时间段（在这种情况下是`Dates.Minute(1)`）。但是，在这种不成立的情况下，舍入行为可能会导致混淆。将[`DateTime`](@ref)舍入到最接近的10小时的预期结果是什么？

```jldoctest
julia> round(DateTime(2016, 7, 17, 11, 55), Dates.Hour(10))
2016-07-17T12:00:00
```

这可能看起来令人困惑，因为小时（12）不能被10整除。选择`2016-07-17T12:00:00`的原因是它是`0000-01-01T00:00:00`之后的17,676,660小时，而17,676,660可以被10整除。

作为 Julia [`Date`](@ref) 和 [`DateTime`](@ref) 的值是根据 ISO 8601 标准表示的，选择了 `0000-01-01T00:00:00` 作为基础（或“舍入纪元”），从这个时间点开始计算用于舍入计算的天数（和毫秒）。 （请注意，这与 Julia 内部表示的 `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` 使用的 [Rata Die notation](https://en.wikipedia.org/wiki/Rata_Die) 略有不同；但由于 ISO 8601 标准对最终用户最为明显，因此选择了 `0000-01-01T00:00:00` 作为舍入纪元，而不是内部使用的 `0000-12-31T00:00:00` 以减少混淆。）

唯一例外是，当四舍五入到周时，使用 `0000-01-01T00:00:00` 作为四舍五入的基准。四舍五入到最近的周将始终返回一个星期一（根据 ISO 8601 规定的周的第一天）。因此，我们在四舍五入到若干周时，使用 `0000-01-03T00:00:00`（根据 ISO 8601 定义的公元 0000 年第一周的第一天）作为基准。

这里有一个相关的案例，其中预期的行为并不一定明显：当我们四舍五入到最近的 `P(2)` 时会发生什么，其中 `P` 是一个 [`Period`](@ref) 类型？在某些情况下（具体来说，当 `P <: Dates.TimePeriod` 时），答案是明确的：

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Hour(2))
2016-07-17T08:00:00

julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Minute(2))
2016-07-17T08:56:00
```

这似乎显而易见，因为每个周期的两个仍然可以均匀地划分到下一个更大的周期中。但是在两个月的情况下（它仍然可以均匀地划分到一年中），答案可能会令人惊讶：

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Month(2))
2016-07-01T00:00:00
```

为什么要四舍五入到七月的第一天，即使它是第7个月（一个奇数）？关键在于月份是从1开始计数的（第一个月被分配为1），与小时、分钟、秒和毫秒不同（它们的第一个值被分配为0）。

这意味着将 [`DateTime`](@ref) 四舍五入到秒、分钟、小时或年（因为 ISO 8601 规范包括零年）的偶数倍将导致该字段中的值为偶数的 `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566`，而将 `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` 四舍五入到月份的偶数倍将导致月份字段具有奇数值。由于月份和年份可能包含不规则的天数，因此四舍五入到偶数天是否会导致天数字段中的值为偶数是不确定的。

请参阅 [API reference](@ref stdlib-dates-api) 以获取有关从 `Dates` 模块导出的方法的更多信息。

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

`Date` 和 `DateTime` 值可以使用 `floor`、`ceil` 或 `round` 方法四舍五入到指定的精度（例如，1 个月或 15 分钟）。

```@docs
Base.floor(::Dates.TimeType, ::Dates.Period)
Base.ceil(::Dates.TimeType, ::Dates.Period)
Base.round(::Dates.TimeType, ::Dates.Period, ::RoundingMode{:NearestTiesUp})
```

大多数 `Period` 值也可以四舍五入到指定的精度：

```@docs
Base.floor(::Dates.ConvertiblePeriod, ::T) where T <: Dates.ConvertiblePeriod
Base.ceil(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod)
Base.round(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod, ::RoundingMode{:NearestTiesUp})
```

以下函数未被导出：

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

一周的天数：

| Variable    | Abbr. | Value (Int) |
|:----------- |:----- |:----------- |
| `Monday`    | `Mon` | 1           |
| `Tuesday`   | `Tue` | 2           |
| `Wednesday` | `Wed` | 3           |
| `Thursday`  | `Thu` | 4           |
| `Friday`    | `Fri` | 5           |
| `Saturday`  | `Sat` | 6           |
| `Sunday`    | `Sun` | 7           |

一月： 二月： 三月： 四月： 五月： 六月： 七月： 八月： 九月： 十月： 十一月： 十二月：

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
