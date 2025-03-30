# Dates

```@meta
DocTestSetup = :(using Dates)
```

`Dates` 모듈은 날짜 작업을 위한 두 가지 유형을 제공합니다: [`Date`](@ref) 및 [`DateTime`](@ref), 각각 일 및 밀리초 정밀도를 나타내며, 둘 다 추상 [`TimeType`](@ref)의 하위 유형입니다. 별도의 유형에 대한 동기는 간단합니다: 일부 작업은 더 높은 정밀도의 복잡성을 다루지 않아도 될 때 코드와 사고 측면에서 훨씬 간단해집니다. 예를 들어, `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` 유형은 단일 날짜의 정밀도(즉, 시간, 분 또는 초가 없음)로만 해결되므로, 시간대, 일광 절약/여름 시간 및 윤초에 대한 일반적인 고려 사항이 필요 없고 피할 수 있습니다.

두 [`Date`](@ref)와 [`DateTime`](@ref)는 기본적으로 불변의 [`Int64`](@ref) 래퍼입니다. 두 타입의 단일 `instant` 필드는 실제로 `UTInstant{P}` 타입으로, UT 초를 기반으로 한 지속적으로 증가하는 기계 타임라인을 나타냅니다 [^1]. `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` 타입은 시간대에 대해 인식하지 않으며 (*naive*, 파이썬 용어로), 자바 8의 *LocalDateTime*에 비유할 수 있습니다. 추가적인 시간대 기능은 [TimeZones.jl package](https://github.com/JuliaTime/TimeZones.jl/)를 통해 추가할 수 있으며, 이는 [IANA time zone database](https://www.iana.org/time-zones)를 컴파일합니다. 두 `4d61726b646f776e2e436f64652822222c2022446174652229_40726566`와 `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566`는 [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) 표준을 기반으로 하며, 이는 프로레프틱 그레고리력에 따릅니다. 한 가지 주의할 점은 ISO 8601 표준이 BC/BCE 날짜에 대해 특별하다는 것입니다. 일반적으로 BC/BCE 시대의 마지막 날인 1-12-31 BC/BCE는 1-1-1 AD/CE로 이어지므로, 0년은 존재하지 않습니다. 그러나 ISO 표준은 1 BC/BCE를 0년으로 간주하므로, `0000-12-31`은 `0001-01-01`의 하루 전이며, 연도 `-0001`(예, 연도에 대해 음수 1)은 2 BC/BCE, 연도 `-0002`는 3 BC/BCE 등입니다.

[^1]: The notion of the UT second is actually quite fundamental. There are basically two different notions of time generally accepted, one based on the physical rotation of the earth (one full rotation = 1 day), the other based on the SI second (a fixed, constant value). These are radically different! Think about it, a "UT second", as defined relative to the rotation of the earth, may have a different absolute length depending on the day! Anyway, the fact that [`Date`](@ref) and [`DateTime`](@ref) are based on UT seconds is a simplifying, yet honest assumption so that things like leap seconds and all their complexity can be avoided. This basis of time is formally called [UT](https://en.wikipedia.org/wiki/Universal_Time) or UT1. Basing types on the UT second basically means that every minute has 60 seconds and every day has 24 hours and leads to more natural calculations when working with calendar dates.

## Constructors

[`Date`](@ref) 및 [`DateTime`](@ref) 유형은 정수 또는 [`Period`](@ref) 유형으로 구성될 수 있으며, 파싱 또는 조정기를 통해 생성될 수 있습니다(조정기에 대한 내용은 나중에 다룰 예정입니다):

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

[`Date`](@ref) 또는 [`DateTime`](@ref) 파싱은 포맷 문자열을 사용하여 수행됩니다. 포맷 문자열은 *구분된* 또는 *고정 너비* "슬롯"을 정의하는 개념에 따라 작동하며, 파싱할 텍스트와 포맷 문자열을 `4d61726b646f776e2e436f64652822222c2022446174652229_40726566` 또는 `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566` 생성자에 전달합니다. 형식은 `Date("2015-01-01",dateformat"y-m-d")` 또는 `DateTime("20150101",dateformat"yyyymmdd")`입니다.

구분된 슬롯은 두 개의 연속된 기간 사이에 파서가 예상해야 하는 구분 기호를 지정하여 표시됩니다. 따라서 `"y-m-d"`는 파서에게 `"2014-07-16"`과 같은 날짜 문자열에서 첫 번째와 두 번째 슬롯 사이에 `-` 문자가 있어야 함을 알려줍니다. `y`, `m`, `d` 문자는 각 슬롯에서 어떤 기간을 파싱해야 하는지를 파서에게 알려줍니다.

위의 생성자 예제인 `Date(2013)`와 같이 구분된 `DateFormat`은 이전 부분이 주어지는 한 날짜와 시간의 일부가 누락될 수 있습니다. 다른 부분은 일반적인 기본값이 주어집니다. 예를 들어, `Date("1981-03", dateformat"y-m-d")`는 `1981-03-01`을 반환하고, `Date("31/12", dateformat"d/m/y")`는 `0001-12-31`을 제공합니다. (기본 연도는 1년 AD/CE입니다.) 그러나 빈 문자열은 항상 `ArgumentError`를 발생시킵니다.

고정 폭 슬롯은 폭에 해당하는 횟수만큼 마침표 문자를 반복하여 지정되며, 문자 사이에 구분자가 없습니다. 따라서 `dateformat"yyyymmdd"`는 `"20140716"`과 같은 날짜 문자열에 해당합니다. 파서는 구분자의 부재로 고정 폭 슬롯을 구분하며, 한 마침표 문자에서 다음 마침표 문자로의 전환인 `"yyyymm"`을 주목합니다.

텍스트 형식의 월 파싱에 대한 지원은 각각 약어 및 전체 길이 월 이름에 대해 `u` 및 `U` 문자를 통해 지원됩니다. 기본적으로 영어 월 이름만 지원되므로 `u`는 "Jan", "Feb", "Mar" 등에 해당합니다. 그리고 `U`는 "January", "February", "March" 등에 해당합니다. 다른 이름=>값 매핑 함수와 유사하게 [`dayname`](@ref) 및 [`monthname`](@ref), 약어 및 전체 이름 월 이름에 대해 각각 `MONTHTOVALUEABBR` 및 `MONTHTOVALUE` 사전에 `locale=>Dict{String,Int}` 매핑을 전달하여 사용자 지정 로케일을 로드할 수 있습니다.

위의 예제에서는 `dateformat""` 문자열 매크로를 사용했습니다. 이 매크로는 매크로가 확장될 때 한 번 `DateFormat` 객체를 생성하고, 코드 조각이 여러 번 실행되더라도 동일한 `DateFormat` 객체를 사용합니다.

```jldoctest
julia> for i = 1:10^5
           Date("2015-01-01", dateformat"y-m-d")
       end
```

또는 DateFormat 객체를 명시적으로 생성할 수 있습니다:

```jldoctest
julia> df = DateFormat("y-m-d");

julia> dt = Date("2015-01-01",df)
2015-01-01

julia> dt2 = Date("2015-01-02",df)
2015-01-02
```

대신 브로드캐스팅을 사용하세요:

```jldoctest
julia> years = ["2015", "2016"];

julia> Date.(years, DateFormat("yyyy"))
2-element Vector{Date}:
 2015-01-01
 2016-01-01
```

편의를 위해 형식 문자열을 직접 전달할 수 있습니다(예: `Date("2015-01-01","y-m-d")`). 그러나 이 형식은 동일한 형식을 반복적으로 구문 분석할 경우 성능 비용이 발생합니다. 매번 내부적으로 새로운 `DateFormat` 객체를 생성하기 때문입니다.

생성자를 통해서뿐만 아니라, `Date` 또는 `DateTime`은 문자열에서 [`parse`](@ref) 및 [`tryparse`](@ref) 함수를 사용하여 생성될 수 있지만, 선택적 세 번째 인수로 `DateFormat` 유형의 형식을 지정할 수 있습니다. 예를 들어, `parse(Date, "06.23.2013", dateformat"m.d.y")` 또는 기본 형식을 사용하는 `tryparse(DateTime, "1999-12-31T23:59:59")`가 있습니다. 두 함수의 주요 차이점은 `4d61726b646f776e2e436f64652822222c202274727970617273652229_40726566`를 사용할 경우 문자열이 비어 있거나 잘못된 형식일 때 오류가 발생하지 않고 대신 `nothing`이 반환된다는 점입니다.

!!! compat "Julia 1.9"
    Julia 1.9 이전에는 빈 문자열이 생성자와 `parse`에 오류 없이 전달될 수 있었으며, 적절하게 `DateTime(1)`, `Date(1)` 또는 `Time(0)`을 반환했습니다. 마찬가지로, `tryparse`는 `nothing`을 반환하지 않았습니다.


전체 구문 분석 및 형식 지정 테스트와 예제는 [`stdlib/Dates/test/io.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/io.jl)에서 확인할 수 있습니다.

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

[`Date`](@ref) 및 [`DateTime`](@ref) 유형은 단일 [`Int64`](@ref) 값으로 저장되므로, 날짜 부분 또는 필드는 접근자 함수를 통해 검색할 수 있습니다. 소문자 접근자는 필드를 정수로 반환합니다:

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

[`Period`](@ref)

```jldoctest tdate
julia> Dates.Year(t)
2014 years

julia> Dates.Day(t)
31 days
```

복합 메서드는 여러 필드에 동시에 접근하는 것이 개별적으로 접근하는 것보다 더 효율적이기 때문에 제공됩니다:

```jldoctest tdate
julia> Dates.yearmonth(t)
(2014, 1)

julia> Dates.monthday(t)
(1, 31)

julia> Dates.yearmonthday(t)
(2014, 1, 31)
```

하나는 기본 `UTInstant` 또는 정수 값을 액세스할 수도 있습니다:

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

쿼리 함수는 [`TimeType`](@ref)에 대한 달력 정보를 제공합니다. 여기에는 요일에 대한 정보가 포함됩니다:

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

연중 월:

```jldoctest tdate2
julia> Dates.monthname(t)
"January"

julia> Dates.daysinmonth(t)
31
```

[`TimeType`](@ref)의 연도와 분기에 대한 정보:

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

[`dayname`](@ref) 및 [`monthname`](@ref) 메서드는 선택적 `locale` 키워드를 사용할 수 있으며, 이를 통해 다른 언어/지역의 요일 또는 월 이름을 반환할 수 있습니다. 또한 약어 이름을 반환하는 이러한 함수의 버전도 있으며, 즉 [`dayabbr`](@ref) 및 [`monthabbr`](@ref)입니다. 먼저 매핑이 `LOCALES` 변수에 로드됩니다:

```jldoctest tdate2
julia> french_months = ["janvier", "février", "mars", "avril", "mai", "juin",
                        "juillet", "août", "septembre", "octobre", "novembre", "décembre"];

julia> french_months_abbrev = ["janv","févr","mars","avril","mai","juin",
                              "juil","août","sept","oct","nov","déc"];

julia> french_days = ["lundi","mardi","mercredi","jeudi","vendredi","samedi","dimanche"];

julia> Dates.LOCALES["french"] = Dates.DateLocale(french_months, french_months_abbrev, french_days, [""]);
```

위에서 언급한 함수들은 쿼리를 수행하는 데 사용될 수 있습니다:

```jldoctest tdate2
julia> Dates.dayname(t;locale="french")
"vendredi"

julia> Dates.monthname(t;locale="french")
"janvier"

julia> Dates.monthabbr(t;locale="french")
"janv"
```

축약된 버전의 요일이 로드되지 않았기 때문에 `dayabbr` 함수를 사용하려고 하면 오류가 발생합니다.

```jldoctest tdate2
julia> Dates.dayabbr(t;locale="french")
ERROR: BoundsError: attempt to access 1-element Vector{String} at index [5]
Stacktrace:
[...]
```

## TimeType-Period Arithmetic

날짜/시간 프레임워크를 사용할 때 날짜-기간 산술이 어떻게 처리되는지 아는 것은 좋은 습관입니다. 왜냐하면 처리해야 할 몇 가지 [tricky issues](https://codeblog.jonskeet.uk/2010/12/01/the-joys-of-date-time-arithmetic/)가 있기 때문입니다 (하루 정밀도 유형에 대해서는 훨씬 덜하지만).

`Dates` 모듈 접근 방식은 [`Period`](@ref) 산술을 수행할 때 가능한 한 적게 변경하려는 간단한 원칙을 따르려고 합니다. 이 접근 방식은 종종 *달력* 산술 또는 누군가가 대화 중에 같은 계산을 물어본다면 아마도 추측할 수 있는 방식으로 알려져 있습니다. 왜 이게 이렇게 중요한가요? 고전적인 예를 들어보겠습니다: 2014년 1월 31일에 1개월을 추가하세요. 답은 무엇인가요? 자바스크립트는 [March 3](https://markhneedham.com/blog/2009/01/07/javascript-add-a-month-to-a-date/) (31일 기준)라고 말합니다. PHP는 [March 2](https://stackoverflow.com/questions/5760262/php-adding-months-to-a-date-while-not-exceeding-the-last-day-of-the-month) (30일 기준)라고 말합니다. 사실, 정답은 없습니다. `Dates` 모듈에서는 2월 28일의 결과를 제공합니다. 어떻게 그렇게 계산할까요? 카지노의 고전적인 7-7-7 도박 게임을 고려해 보세요.

이제 7-7-7 대신 슬롯이 연도-월-일 형식이라고 상상해 보세요. 예를 들어, 2014-01-31입니다. 이 날짜에 1개월을 추가하라고 요청하면, 월 슬롯이 증가하여 이제 2014-02-31이 됩니다. 그런 다음, 일 숫자가 새 월의 마지막 유효 일보다 큰지 확인합니다. 만약 그렇다면(위의 경우처럼), 일 숫자는 마지막 유효 일(28)로 조정됩니다. 이 접근 방식의 결과는 무엇일까요? 날짜에 또 다른 월을 추가해 보세요, `2014-02-28 + Month(1) == 2014-03-28`. 뭐라고요? 3월의 마지막 날을 기대하셨나요? 아닙니다, 죄송합니다. 7-7-7 슬롯을 기억하세요. 가능한 한 적은 슬롯이 변경되므로, 먼저 월 슬롯을 1만큼 증가시킵니다. 2014-03-28이 되고, 끝났습니다. 이는 유효한 날짜이기 때문입니다. 반면, 원래 날짜인 2014-01-31에 2개월을 추가하면, 예상대로 2014-03-31이 됩니다. 이 접근 방식의 또 다른 결과는 특정 순서가 강제될 때 결합 법칙이 손실된다는 것입니다(즉, 다른 순서로 추가하면 다른 결과가 나옵니다). 예를 들어:

```jldoctest
julia> (Date(2014,1,29)+Dates.Day(1)) + Dates.Month(1)
2014-02-28

julia> (Date(2014,1,29)+Dates.Month(1)) + Dates.Day(1)
2014-03-01
```

무슨 일이 일어나고 있나요? 첫 번째 줄에서는 1일을 1월 29일에 추가하고, 그 결과 2014-01-30이 됩니다. 그런 다음 1개월을 추가하면 2014-02-30이 되고, 이는 2014-02-28로 조정됩니다. 두 번째 예에서는 먼저 1개월을 추가하여 2014-02-29가 되고, 이는 2014-02-28로 조정된 다음, 1일을 추가하여 2014-03-01이 됩니다. 이 경우에 도움이 되는 디자인 원칙 중 하나는 여러 기간이 있을 때, 연산이 기간의 *유형*에 따라 순서가 정해진다는 것입니다. 즉, `Year`가 항상 먼저 추가되고, 그 다음에 `Month`, `Week` 등이 추가됩니다. 따라서 다음은 *결합법칙*을 결과적으로 보장하며 잘 작동합니다:

```jldoctest
julia> Date(2014,1,29) + Dates.Day(1) + Dates.Month(1)
2014-03-01

julia> Date(2014,1,29) + Dates.Month(1) + Dates.Day(1)
2014-03-01
```

교묘한가? 아마도. 순진한 `Dates` 사용자는 무엇을 해야 할까요? 핵심은 특정 결합성을 명시적으로 강제하는 것이 월을 다룰 때 예상치 못한 결과를 초래할 수 있다는 점을 인식하는 것입니다. 그렇지 않으면 모든 것이 예상대로 작동해야 합니다. 다행히도, UT에서 시간을 다룰 때 날짜-기간 산술에서의 이상한 경우는 이 정도가 전부입니다 (일광 절약 시간, 윤초 등을 다루는 "즐거움"을 피하면서).

보너스로, 모든 기간 산술 객체는 범위와 직접 작동합니다:

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

날짜-기간 산술이 편리하긴 하지만, 종종 날짜에 필요한 계산은 고정된 기간의 수보다는 *달력적* 또는 *시간적* 성격을 띠게 됩니다. 휴일이 그 좋은 예입니다. 대부분 "메모리얼 데이 = 5월의 마지막 월요일" 또는 "추수감사절 = 11월의 4번째 목요일"과 같은 규칙을 따릅니다. 이러한 종류의 시간적 표현은 월의 첫 번째 또는 마지막, 다음 화요일, 첫 번째 및 세 번째 수요일 등과 같이 달력에 상대적인 규칙을 다룹니다.

`Dates` 모듈은 시간 규칙을 간단하고 간결하게 표현하는 데 도움이 되는 여러 편리한 메서드를 통해 *조정기* API를 제공합니다. 조정기 메서드의 첫 번째 그룹은 주, 월, 분기 및 연도의 첫 번째와 마지막을 다룹니다. 이들은 각각 단일 [`TimeType`](@ref)를 입력으로 받아 원하는 기간의 첫 번째 또는 마지막으로 *조정*하여 반환합니다.

```jldoctest
julia> Dates.firstdayofweek(Date(2014,7,16)) # Adjusts the input to the Monday of the input's week
2014-07-14

julia> Dates.lastdayofmonth(Date(2014,7,16)) # Adjusts to the last day of the input's month
2014-07-31

julia> Dates.lastdayofquarter(Date(2014,7,16)) # Adjusts to the last day of the input's quarter
2014-09-30
```

다음 두 개의 고차 방법인 [`tonext`](@ref)와 [`toprev`](@ref)는 시작 [`TimeType`](@ref)와 함께 첫 번째 인수로 `DateFunction`을 사용하여 시간 표현을 처리하는 방법을 일반화합니다. `DateFunction`은 단일 `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566`를 입력으로 받아 [`Bool`](@ref)를 반환하는 함수로, 일반적으로 익명입니다. `true`는 만족스러운 조정 기준을 나타냅니다. 예를 들어:

```jldoctest
julia> istuesday = x->Dates.dayofweek(x) == Dates.Tuesday; # Returns true if the day of the week of x is Tuesday

julia> Dates.tonext(istuesday, Date(2014,7,13)) # 2014-07-13 is a Sunday
2014-07-15

julia> Dates.tonext(Date(2014,7,13), Dates.Tuesday) # Convenience method provided for day of the week adjustments
2014-07-15
```

이것은 더 복잡한 시간 표현을 위한 do-block 구문과 함께 유용합니다:

```jldoctest
julia> Dates.tonext(Date(2014,7,13)) do x
           # Return true on the 4th Thursday of November (Thanksgiving)
           Dates.dayofweek(x) == Dates.Thursday &&
           Dates.dayofweekofmonth(x) == 4 &&
           Dates.month(x) == Dates.November
       end
2014-11-27
```

[`Base.filter`](@ref) 메소드는 지정된 범위 내의 모든 유효한 날짜/순간을 얻는 데 사용할 수 있습니다:

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

추가 예제 및 테스트는 [`stdlib/Dates/test/adjusters.jl`](https://github.com/JuliaLang/julia/blob/master/stdlib/Dates/test/adjusters.jl)에서 확인할 수 있습니다.

## Period Types

기간은 인간이 보는 불연속적이고 때때로 불규칙한 시간의 지속입니다. 1개월을 고려해보면, 연도와 월의 맥락에 따라 28, 29, 30 또는 31일을 나타낼 수 있습니다. 또는 윤년의 경우 1년은 365일 또는 366일을 나타낼 수 있습니다. [`Period`](@ref) 유형은 간단한 [`Int64`](@ref) 래퍼이며, 모든 `Int64` 변환 가능 유형을 래핑하여 구성됩니다. 즉, `Year(1)` 또는 `Month(3.0)`과 같습니다. 동일한 유형의 `4d61726b646f776e2e436f64652822222c2022506572696f642229_40726566` 간의 산술 연산은 정수처럼 작동하며, 제한된 `Period-Real` 산술 연산이 가능합니다. 기본 정수를 추출하려면 [`Dates.value`](@ref)를 사용할 수 있습니다.

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

비정수 배수의 기간이나 지속 시간을 표현하는 것은 [`Dates.CompoundPeriod`](@ref) 유형을 사용하여 달성할 수 있습니다. 복합 기간은 간단한 [`Period`](@ref) 유형에서 수동으로 구성할 수 있습니다. 또한, [`canonicalize`](@ref) 함수를 사용하여 기간을 `4d61726b646f776e2e436f64652822222c202244617465732e436f6d706f756e64506572696f642229_40726566`로 분해할 수 있습니다. 이는 두 개의 `DateTime` 간의 차이와 같은 지속 시간을 보다 편리한 표현으로 변환하는 데 특히 유용합니다.

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

[`Date`](@ref) 및 [`DateTime`](@ref) 값은 [`floor`](@ref), [`ceil`](@ref), 또는 [`round`](@ref)를 사용하여 지정된 해상도(예: 1개월 또는 15분)로 반올림할 수 있습니다.

```jldoctest
julia> floor(Date(1985, 8, 16), Dates.Month)
1985-08-01

julia> ceil(DateTime(2013, 2, 13, 0, 31, 20), Dates.Minute(15))
2013-02-13T00:45:00

julia> round(DateTime(2016, 8, 6, 20, 15), Dates.Day)
2016-08-07T00:00:00
```

숫자 [`round`](@ref) 방법과 달리, 기본적으로 짝수 쪽으로 동점을 깨는 이 방법은 [`TimeType`](@ref)`4d61726b646f776e2e436f64652822222c2022726f756e642229_40726566` 방법은 `RoundNearestTiesUp` 반올림 모드를 사용합니다. (가장 가까운 "짝수" `4d61726b646f776e2e436f64652822222c202254696d65547970652229_40726566`로 동점을 깨는 것이 무엇을 의미하는지 추측하기 어렵습니다.) 사용 가능한 `RoundingMode`에 대한 자세한 내용은 [API reference](@ref stdlib-dates-api)에서 확인할 수 있습니다.

반올림은 일반적으로 예상대로 작동해야 하지만, 예상되는 동작이 명확하지 않은 몇 가지 경우가 있습니다.

### Rounding Epoch

많은 경우, 반올림을 위해 지정된 해상도(예: `Dates.Second(30)`)는 다음으로 큰 주기(이 경우 `Dates.Minute(1)`)에 정확히 나누어 떨어집니다. 그러나 이러한 경우에 반올림 동작이 그렇지 않은 경우에는 혼란을 초래할 수 있습니다. [`DateTime`](@ref)를 가장 가까운 10시간으로 반올림할 때 예상되는 결과는 무엇인가요?

```jldoctest
julia> round(DateTime(2016, 7, 17, 11, 55), Dates.Hour(10))
2016-07-17T12:00:00
```

그것은 혼란스러울 수 있습니다. 왜냐하면 시간(12)은 10으로 나눌 수 없기 때문입니다. `2016-07-17T12:00:00`이 선택된 이유는 `0000-01-01T00:00:00` 이후 17,676,660시간이 경과했으며, 17,676,660은 10으로 나눌 수 있기 때문입니다.

줄리아 [`Date`](@ref) 및 [`DateTime`](@ref) 값은 ISO 8601 표준에 따라 표현되며, 날짜(및 밀리초) 계산의 반올림 계산을 시작하기 위해 `0000-01-01T00:00:00`이 기준(또는 "반올림 기준점")으로 선택되었습니다. (이는 줄리아의 내부 표현인 `4d61726b646f776e2e436f64652822222c2022446174652229_40726566`가 [Rata Die notation](https://en.wikipedia.org/wiki/Rata_Die)를 사용하여 약간 다르다는 점에 유의하십시오. 그러나 ISO 8601 표준이 최종 사용자에게 가장 잘 보이기 때문에 혼란을 최소화하기 위해 내부적으로 사용되는 `0000-12-31T00:00:00` 대신 `0000-01-01T00:00:00`이 반올림 기준점으로 선택되었습니다.)

`0000-01-01T00:00:00`를 반올림 기준으로 사용하는 유일한 예외는 주 단위로 반올림할 때입니다. 가장 가까운 주로 반올림할 경우 항상 월요일(ISO 8601에 의해 지정된 주의 첫 번째 날)이 반환됩니다. 이러한 이유로, 주 단위로 반올림할 때는 `0000-01-03T00:00:00`(ISO 8601에 의해 정의된 0000년 첫 주의 첫 번째 날)을 기준으로 사용합니다.

여기 예상되는 동작이 반드시 명확하지 않은 관련 사례가 있습니다: `P(2)`에 가장 가까운 값으로 반올림할 때 어떤 일이 발생할까요? 여기서 `P`는 [`Period`](@ref) 유형입니다. 특정 경우(특히 `P <: Dates.TimePeriod`인 경우)에는 답이 명확합니다:

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Hour(2))
2016-07-17T08:00:00

julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Minute(2))
2016-07-17T08:56:00
```

이것은 명백해 보입니다. 왜냐하면 이러한 각 주기의 두 배가 여전히 다음 더 큰 주기로 고르게 나누어지기 때문입니다. 그러나 두 달의 경우(여전히 1년으로 고르게 나누어짐) 답은 놀라울 수 있습니다:

```jldoctest
julia> round(DateTime(2016, 7, 17, 8, 55, 30), Dates.Month(2))
2016-07-01T00:00:00
```

왜 7월의 첫째 날로 반올림하나요? 7은 홀수인데 말이죠. 핵심은 월이 1부터 시작된다는 것입니다(첫 번째 월은 1로 할당됨). 반면, 시간, 분, 초, 밀리초는 0부터 시작합니다.

이것은 [`DateTime`](@ref)를 초, 분, 시간 또는 연도의 짝수 배수로 반올림하면 해당 필드에서 짝수 값을 가지는 `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566`가 생성된다는 것을 의미합니다(ISO 8601 사양에는 연도 0이 포함되기 때문입니다). 반면, `4d61726b646f776e2e436f64652822222c20224461746554696d652229_40726566`를 월의 짝수 배수로 반올림하면 월 필드가 홀수 값을 가지게 됩니다. 월과 연도 모두 불규칙한 일 수를 포함할 수 있기 때문에, 짝수 일 수로 반올림했을 때 일 필드에서 짝수 값이 생성될지는 불확실합니다.

`Dates` 모듈에서 내보낸 메서드에 대한 추가 정보는 [API reference](@ref stdlib-dates-api)를 참조하세요.

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

`Date` 및 `DateTime` 값은 `floor`, `ceil` 또는 `round`를 사용하여 지정된 해상도(예: 1개월 또는 15분)로 반올림할 수 있습니다.

```@docs
Base.floor(::Dates.TimeType, ::Dates.Period)
Base.ceil(::Dates.TimeType, ::Dates.Period)
Base.round(::Dates.TimeType, ::Dates.Period, ::RoundingMode{:NearestTiesUp})
```

대부분의 `Period` 값은 지정된 해상도로 반올림할 수도 있습니다:

```@docs
Base.floor(::Dates.ConvertiblePeriod, ::T) where T <: Dates.ConvertiblePeriod
Base.ceil(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod)
Base.round(::Dates.ConvertiblePeriod, ::Dates.ConvertiblePeriod, ::RoundingMode{:NearestTiesUp})
```

다음 함수는 내보내지지 않습니다:

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

요일:

| Variable    | Abbr. | Value (Int) |
|:----------- |:----- |:----------- |
| `Monday`    | `Mon` | 1           |
| `Tuesday`   | `Tue` | 2           |
| `Wednesday` | `Wed` | 3           |
| `Thursday`  | `Thu` | 4           |
| `Friday`    | `Fri` | 5           |
| `Saturday`  | `Sat` | 6           |
| `Sunday`    | `Sun` | 7           |

연중 월:

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
