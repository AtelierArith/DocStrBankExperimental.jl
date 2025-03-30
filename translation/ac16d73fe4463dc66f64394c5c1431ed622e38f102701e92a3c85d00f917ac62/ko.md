# Running External Programs

줄리아는 셸, 펄, 루비에서 명령어를 위한 백틱 표기법을 차용합니다. 그러나 줄리아에서는 다음과 같이 작성합니다.

```jldoctest
julia> `echo hello`
`echo hello`
```

여러 셸, Perl 또는 Ruby의 동작과 여러 측면에서 다릅니다:

  * 즉시 명령을 실행하는 대신, 백틱은 명령을 나타내기 위해 [`Cmd`](@ref) 객체를 생성합니다. 이 객체를 사용하여 명령을 다른 명령과 파이프를 통해 연결할 수 있습니다. [`run`](@ref) 그것과, 그리고 [`read`](@ref) 또는 [`write`](@ref) 그것에 연결할 수 있습니다.
  * 명령이 실행될 때, Julia는 특별히 설정하지 않는 한 그 출력을 캡처하지 않습니다. 대신, 명령의 출력은 기본적으로 [`stdout`](@ref)로 전송되며, 이는 `libc`의 `system` 호출을 사용할 때와 같습니다.
  * 명령은 절대 셸과 함께 실행되지 않습니다. 대신, Julia는 명령 구문을 직접 구문 분석하고, 변수를 적절하게 보간하며, 셸이 하는 것처럼 단어를 기준으로 분할하여 셸 인용 구문을 존중합니다. 명령은 `julia`의 즉각적인 자식 프로세스로 실행되며, `fork` 및 `exec` 호출을 사용합니다.

!!! note
    다음은 Linux 또는 MacOS와 같은 Posix 환경을 가정합니다. Windows에서는 `echo` 및 `dir`과 같은 많은 유사한 명령이 외부 프로그램이 아니라 `cmd.exe` 자체에 내장되어 있습니다. 이러한 명령을 실행하는 한 가지 옵션은 `cmd.exe`를 호출하는 것입니다. 예를 들어 `cmd /C echo hello`와 같이 사용할 수 있습니다. 또는 Julia를 Cygwin과 같은 Posix 환경 내에서 실행할 수 있습니다.


여기 외부 프로그램을 실행하는 간단한 예가 있습니다:

```jldoctest
julia> mycommand = `echo hello`
`echo hello`

julia> typeof(mycommand)
Cmd

julia> run(mycommand);
hello
```

`hello`는 `echo` 명령의 출력으로, [`stdout`](@ref)에 전송됩니다. 외부 명령이 성공적으로 실행되지 않으면, run 메서드는 [`ProcessFailedException`](@ref)을 던집니다.

외부 명령의 출력을 읽고 싶다면, [`read`](@ref) 또는 [`readchomp`](@ref)를 대신 사용할 수 있습니다:

```jldoctest
julia> read(`echo hello`, String)
"hello\n"

julia> readchomp(`echo hello`)
"hello"
```

더 일반적으로, [`open`](@ref)를 사용하여 외부 명령에서 읽거나 쓸 수 있습니다.

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

프로그램 이름과 명령의 개별 인수는 명령이 문자열 배열인 것처럼 접근하고 반복할 수 있습니다:

```jldoctest
julia> collect(`echo "foo bar"`)
2-element Vector{String}:
 "echo"
 "foo bar"

julia> `echo "foo bar"`[2]
"foo bar"
```

## [Interpolation](@id command-interpolation)

파일의 이름을 변수 `file`에 사용하여 명령의 인수로 전달하고 싶다고 가정해 보겠습니다. 문자열 리터럴에서처럼 `$`를 사용하여 보간할 수 있습니다 (참조: [Strings](@ref)):

```jldoctest
julia> file = "/etc/passwd"
"/etc/passwd"

julia> `sort $file`
`sort /etc/passwd`
```

외부 프로그램을 셸을 통해 실행할 때 흔히 발생하는 함정 중 하나는 파일 이름에 셸에 특수한 문자가 포함되어 있을 경우 원치 않는 동작을 유발할 수 있다는 것입니다. 예를 들어, `/etc/passwd` 대신 `/Volumes/External HD/data.csv` 파일의 내용을 정렬하고 싶다고 가정해 보겠습니다. 한번 시도해 보겠습니다:

```jldoctest
julia> file = "/Volumes/External HD/data.csv"
"/Volumes/External HD/data.csv"

julia> `sort $file`
`sort '/Volumes/External HD/data.csv'`
```

파일 이름이 어떻게 인용되었나요? 줄리아는 `file`이 단일 인수로 보간될 것임을 알고 있으므로, 단어를 대신 인용해 줍니다. 사실, 이는 정확하지 않습니다: `file`의 값은 결코 셸에 의해 해석되지 않으므로 실제 인용이 필요하지 않습니다; 인용은 사용자에게 표시하기 위해서만 삽입됩니다. 이는 셸 단어의 일부로 값을 보간하더라도 작동합니다:

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

보시다시피, `path` 변수의 공백이 적절하게 이스케이프 처리되었습니다. 하지만 여러 단어를 *삽입*하고 싶다면 어떻게 해야 할까요? 그런 경우에는 배열(또는 다른 반복 가능한 컨테이너)을 사용하면 됩니다:

```jldoctest
julia> files = ["/etc/passwd","/Volumes/External HD/data.csv"]
2-element Vector{String}:
 "/etc/passwd"
 "/Volumes/External HD/data.csv"

julia> `grep foo $files`
`grep foo /etc/passwd '/Volumes/External HD/data.csv'`
```

배열을 셸 단어의 일부로 보간하면, Julia는 셸의 `{a,b,c}` 인수 생성을 에뮬레이트합니다:

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> `grep xylophone $names.txt`
`grep xylophone foo.txt bar.txt baz.txt`
```

또한, 여러 배열을 동일한 단어에 보간하면 셸의 데카르트 곱 생성 동작이 에뮬레이트됩니다:

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

리터럴 배열을 보간할 수 있으므로, 먼저 임시 배열 객체를 생성할 필요 없이 이 생성 기능을 사용할 수 있습니다:

```jldoctest
julia> `rm -rf $["foo","bar","baz","qux"].$["aux","log","pdf"]`
`rm -rf foo.aux foo.log foo.pdf bar.aux bar.log bar.pdf baz.aux baz.log baz.pdf qux.aux qux.log qux.pdf`
```

## Quoting

불가피하게, 사람들은 그리 간단하지 않은 명령어를 작성하고 싶어지며, 인용부호를 사용하는 것이 필요해집니다. 다음은 셸 프롬프트에서의 간단한 Perl 원라이너 예제입니다:

```
sh$ perl -le '$|=1; for (0..3) { print }'
0
1
2
3
```

Perl 표현식은 두 가지 이유로 단일 따옴표로 묶여야 합니다: 공백이 표현식을 여러 개의 셸 단어로 나누지 않도록 하기 위해서와 `$|`와 같은 Perl 변수의 사용이 보간(interpolation)을 일으키지 않도록 하기 위해서입니다. 다른 경우에는 보간이 발생하도록 하기 위해서 이중 따옴표를 사용할 수 있습니다:

```
sh$ first="A"
sh$ second="B"
sh$ perl -le '$|=1; print for @ARGV' "1: $first" "2: $second"
1: A
2: B
```

일반적으로, Julia의 백틱 구문은 셸 명령어를 그대로 잘라서 붙여넣을 수 있도록 신중하게 설계되었습니다. 이 경우 이스케이프, 인용 및 보간 동작은 셸과 동일합니다. 유일한 차이점은 보간이 통합되어 있으며 Julia의 단일 문자열 값과 여러 값의 컨테이너에 대한 개념을 인식한다는 것입니다. 위의 두 예제를 Julia에서 시도해 봅시다:

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

결과는 동일하며, 줄리아의 보간 동작은 몇 가지 개선 사항과 함께 셸의 동작을 모방합니다. 이는 줄리아가 1급 iterable 객체를 지원하는 반면 대부분의 셸은 이를 위해 공백으로 분할된 문자열을 사용하여 모호성을 초래하기 때문입니다. 셸 명령을 줄리아로 포팅하려고 할 때는 먼저 잘라내고 붙여넣기를 시도해 보세요. 줄리아는 명령을 실행하기 전에 보여주므로, 손상 없이 그 해석을 쉽게 안전하게 검토할 수 있습니다.

## Pipelines

쉘 메타문자, 예를 들어 `|`, `&`, 및 `>`는 줄리아의 백틱 안에서 따옴표로 묶거나 이스케이프해야 합니다:

```jldoctest
julia> run(`echo hello '|' sort`);
hello | sort

julia> run(`echo hello \| sort`);
hello | sort
```

이 표현식은 `echo` 명령을 세 개의 단어인 `hello`, `|`, `sort`를 인수로 호출합니다. 그 결과는 단일 행이 출력됩니다: `hello | sort`. 그렇다면 파이프라인은 어떻게 구성할까요? 백틱 안에 `'|'`를 사용하는 대신, [`pipeline`](@ref)를 사용합니다:

```jldoctest
julia> run(pipeline(`echo hello`, `sort`));
hello
```

이것은 `echo` 명령의 출력을 `sort` 명령으로 파이프합니다. 물론, 정렬할 줄이 하나뿐이기 때문에 이것은 그리 흥미롭지 않지만, 우리는 확실히 훨씬 더 흥미로운 작업을 할 수 있습니다:

```julia-repl
julia> run(pipeline(`cut -d: -f3 /etc/passwd`, `sort -n`, `tail -n5`))
210
211
212
213
214
```

이것은 UNIX 시스템에서 가장 높은 다섯 개의 사용자 ID를 출력합니다. `cut`, `sort` 및 `tail` 명령은 모두 현재 `julia` 프로세스의 즉각적인 자식으로 생성되며, 중간에 셸 프로세스가 없습니다. Julia 자체가 셸에서 일반적으로 수행되는 파이프 설정 및 파일 설명자 연결 작업을 수행합니다. Julia가 이를 직접 수행하기 때문에 더 나은 제어를 유지하고 셸에서는 할 수 없는 몇 가지 작업을 수행할 수 있습니다.

줄리아는 여러 명령을 병렬로 실행할 수 있습니다:

```jldoctest; filter = r"(world\nhello|hello\nworld)"
julia> run(`echo hello` & `echo world`);
world
hello
```

출력의 순서는 비결정적입니다. 두 개의 `echo` 프로세스가 거의 동시에 시작되며, 서로 공유하는 [`stdout`](@ref) 디스크립터에 첫 번째로 쓰기 위해 경쟁하기 때문입니다. Julia는 이 두 프로세스의 출력을 다른 프로그램으로 파이프할 수 있도록 해줍니다:

```jldoctest
julia> run(pipeline(`echo world` & `echo hello`, `sort`));
hello
world
```

UNIX 배관 측면에서 여기서 일어나는 일은 단일 UNIX 파이프 객체가 생성되고 두 `echo` 프로세스에 의해 쓰여지며, 파이프의 다른 쪽 끝은 `sort` 명령에 의해 읽힌다는 것입니다.

IO 리디렉션은 `pipeline` 함수에 키워드 인수 `stdin`, `stdout`, 및 `stderr`를 전달하여 수행할 수 있습니다:

```julia
pipeline(`do_work`, stdout=pipeline(`sort`, "out.txt"), stderr="errs.txt")
```

### Avoiding Deadlock in Pipelines

파이프라인의 양쪽 끝에서 단일 프로세스가 읽고 쓸 때, 커널이 모든 데이터를 버퍼링하도록 강제하는 것을 피하는 것이 중요합니다.

예를 들어, 명령의 모든 출력을 읽을 때는 `read(out, String)`을 호출하고 `wait(process)`를 호출하지 마십시오. 전자는 프로세스에 의해 작성된 모든 데이터를 적극적으로 소비하는 반면, 후자는 리더가 연결될 때까지 데이터를 커널의 버퍼에 저장하려고 시도합니다.

또 다른 일반적인 해결책은 파이프라인의 리더와 라이터를 별도의 [`Task`](@ref)로 분리하는 것입니다:

```julia
writer = @async write(process, "data")
reader = @async do_compute(read(process, String))
wait(writer)
fetch(reader)
```

(일반적으로 독자는 별도의 작업이 아니며, 어쨌든 즉시 `fetch`하므로 그렇습니다).

### Complex Example

고급 프로그래밍 언어, 일급 명령 추상화, 그리고 프로세스 간의 파이프 자동 설정의 조합은 강력합니다. 쉽게 생성할 수 있는 복잡한 파이프라인의 감각을 제공하기 위해, 다음은 다소 정교한 예시들입니다. Perl 원라이너의 과도한 사용에 대해 사과드립니다:

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

이것은 단일 생산자가 두 개의 동시 소비자에게 데이터를 공급하는 고전적인 예입니다: 하나의 `perl` 프로세스가 0부터 5까지의 숫자가 있는 줄을 생성하고, 두 개의 병렬 프로세스가 그 출력을 소비합니다. 하나는 줄에 "A"라는 글자를 접두사로 붙이고, 다른 하나는 "B"라는 글자를 붙입니다. 첫 번째 줄을 어떤 소비자가 가져가는지는 비결정적이지만, 일단 그 경쟁에서 승리하면 줄은 한 프로세스가 소비한 후 다른 프로세스가 소비하는 방식으로 번갈아 소비됩니다. Perl에서 `$|=1`을 설정하면 각 print 문이 [`stdout`](@ref) 핸들을 플러시하게 되어 이 예제가 작동하는 데 필요합니다. 그렇지 않으면 모든 출력이 버퍼링되어 한 번에 파이프에 인쇄되고 단지 하나의 소비자 프로세스가 읽게 됩니다.

여기 훨씬 더 복잡한 다단계 생산자-소비자 예제가 있습니다:

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

이 예제는 이전 예제와 유사하지만, 소비자가 두 단계로 나뉘어 있으며 각 단계는 서로 다른 대기 시간을 가지고 있어 포화된 처리량을 유지하기 위해 서로 다른 수의 병렬 작업자를 사용합니다.

이 모든 예제를 시도해 보시기를 강력히 권장합니다. 어떻게 작동하는지 확인해 보세요.

## `Cmd` Objects

백틱 구문은 [`Cmd`](@ref) 유형의 객체를 생성합니다. 이러한 객체는 기존 `Cmd` 또는 인수 목록에서 직접 구성할 수도 있습니다:

```julia
run(Cmd(`pwd`, dir=".."))
run(Cmd(["pwd"], detach=true, ignorestatus=true))
```

이것은 키워드 인수를 통해 `Cmd`의 실행 환경의 여러 측면을 지정할 수 있게 해줍니다. 예를 들어, `dir` 키워드는 `Cmd`의 작업 디렉토리를 제어하는 기능을 제공합니다:

```jldoctest
julia> run(Cmd(`pwd`, dir="/"));
/
```

`env` 키워드를 사용하면 실행 환경 변수를 설정할 수 있습니다:

```jldoctest
julia> run(Cmd(`sh -c "echo foo \$HOWLONG"`, env=("HOWLONG" => "ever!",)));
foo ever!
```

[`Cmd`](@ref)에 대한 추가 키워드 인수를 참조하십시오. [`setenv`](@ref) 및 [`addenv`](@ref) 명령은 각각 `Cmd` 실행 환경 변수를 교체하거나 추가하는 또 다른 수단을 제공합니다:

```jldoctest
julia> run(setenv(`sh -c "echo foo \$HOWLONG"`, ("HOWLONG" => "ever!",)));
foo ever!

julia> run(addenv(`sh -c "echo foo \$HOWLONG"`, "HOWLONG" => "ever!"));
foo ever!
```
