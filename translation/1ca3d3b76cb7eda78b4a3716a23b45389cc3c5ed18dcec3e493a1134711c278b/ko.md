# [Command-line Interface](@id cli)

## Using arguments inside scripts

`julia`를 사용하여 스크립트를 실행할 때, 스크립트에 추가 인수를 전달할 수 있습니다:

```
$ julia script.jl arg1 arg2...
```

이 추가적인 명령줄 인수는 전역 상수 `ARGS`에 전달됩니다. 스크립트 자체의 이름은 전역 `PROGRAM_FILE`로 전달됩니다. 명령줄에서 `-e` 옵션을 사용하여 줄리아 표현식이 주어질 때 `ARGS`도 설정되지만 `PROGRAM_FILE`은 비어 있다는 점에 유의하세요. 예를 들어, 스크립트에 주어진 인수를 단순히 출력하려면 다음과 같이 할 수 있습니다:

```
$ julia -e 'println(PROGRAM_FILE); for x in ARGS; println(x); end' foo bar

foo
bar
```

코드를 스크립트에 넣고 실행할 수도 있습니다:

```
$ echo 'println(PROGRAM_FILE); for x in ARGS; println(x); end' > script.jl
$ julia script.jl foo bar
script.jl
foo
bar
```

`--` 구분자는 스크립트 파일을 위한 명령줄 인수와 Julia를 위한 인수를 구분하는 데 사용할 수 있습니다:

```
$ julia --color=yes -O -- script.jl arg1 arg2..
```

자세한 Julia 스크립트 작성에 대한 정보는 [Scripting](@ref man-scripting)를 참조하세요.

## The `Main.main` entry point

Julia 1.11부터 `Base`는 매크로 `@main`을 내보냅니다. 이 매크로는 기호 `main`으로 확장되지만, 스크립트나 표현식 실행이 끝나면 `julia`는 `Main.main(ARGS)`라는 함수를 실행하려고 시도합니다. 이 함수가 정의되어 있고 `@main` 매크로를 사용하여 이 동작을 선택한 경우에 해당합니다.

이 기능은 컴파일된 워크플로우와 대화형 워크플로우의 통합을 돕기 위해 설계되었습니다. 컴파일된 워크플로우에서는 `main` 함수를 정의하는 코드의 로딩이 호출과 공간적 및 시간적으로 분리될 수 있습니다. 그러나 대화형 워크플로우의 경우, 평가된 스크립트나 표현식의 끝에서 `exit(main(ARGS))`를 명시적으로 호출하는 것과 동등한 동작을 합니다.

!!! compat "Julia 1.11"
    특별 진입점 `Main.main`은 Julia 1.11에 추가되었습니다. 이전 Julia 버전과의 호환성을 위해 스크립트 끝에 명시적으로 `@isdefined(var"@main") ? (@main) : exit(main(ARGS))`를 추가하세요.


이 기능이 작동하는 모습을 보려면, 다음 정의를 고려하세요. 이는 `main`에 대한 명시적인 호출이 없더라도 print 함수를 실행합니다:

```
$ julia -e '(@main)(args) = println("Hello World!")'
Hello World!
$
```

`Main` 모듈의 `main` 바인딩만 이 동작을 가지며, 이는 정의 모듈 내에서 매크로 `@main`이 사용된 경우에만 해당됩니다.

예를 들어, `main` 대신 `hello`를 사용하면 `hello` 함수가 실행되지 않습니다:

```
$ julia -e 'hello(ARGS) = println("Hello World!")'
$
```

그리고 `main`의 단순한 정의도 그렇지 않을 것입니다:

```
$ julia -e 'main(ARGS) = println("Hello World!")'
$
```

그러나 옵트인(opt-in)은 정의 시점에서 발생할 필요는 없습니다:

```
$ julia -e 'main(ARGS) = println("Hello World!"); @main'
Hello World!
$
```

`main` 바인딩은 패키지에서 가져올 수 있습니다. *헬로 월드* 패키지는 다음과 같이 정의됩니다.

```
module Hello

export main
(@main)(args) = println("Hello from the package!")

end
```

다음과 같이 사용될 수 있습니다:

```
$ julia -e 'using Hello'
Hello from the package!
$ julia -e 'import Hello' # N.B.: Execution depends on the binding not whether the package is loaded
$
```

그러나 현재의 모범 사례 권장 사항은 애플리케이션 코드와 재사용 가능한 라이브러리 코드를 동일한 패키지에 혼합하지 않는 것입니다. 헬퍼 애플리케이션은 별도의 패키지로 배포되거나 패키지의 `bin` 폴더에 있는 별도의 `main` 진입점이 있는 스크립트로 배포될 수 있습니다.

## Parallel mode

줄리아는 `-p` 또는 `--machine-file` 옵션을 사용하여 병렬 모드로 시작할 수 있습니다. `-p n`은 추가로 `n` 개의 작업자 프로세스를 시작하며, `--machine-file file`은 파일 `file`의 각 줄에 대해 작업자를 시작합니다. `file`에 정의된 머신은 비밀번호 없는 `ssh` 로그인을 통해 접근 가능해야 하며, 줄리아는 현재 호스트와 동일한 위치에 설치되어 있어야 합니다. 각 머신 정의는 `[count*][user@]host[:port] [bind_addr[:port]]` 형식을 따릅니다. `user`는 현재 사용자로 기본 설정되며, `port`는 표준 ssh 포트로 설정됩니다. `count`는 노드에서 생성할 작업자의 수이며 기본값은 1입니다. 선택적 `bind-to bind_addr[:port]`는 다른 작업자가 이 작업자에 연결하는 데 사용할 IP 주소와 포트를 지정합니다.

## Startup file

Julia를 실행할 때마다 실행되기를 원하는 코드가 있다면, `~/.julia/config/startup.jl`에 넣을 수 있습니다:

```
$ echo 'println("Greetings! 你好! 안녕하세요?")' > ~/.julia/config/startup.jl
$ julia
Greetings! 你好! 안녕하세요?

...
```

`~/.julia` 디렉토리는 Julia를 처음 실행한 후에 생성되지만, 이를 사용하는 경우 `~/.julia/config` 폴더와 `~/.julia/config/startup.jl` 파일을 생성해야 할 수도 있습니다.

[The Julia REPL](@ref)에서만 스타트업 코드를 실행하고 (`julia`가 스크립트에서 실행될 때는 실행되지 않도록) `startup.jl`에서 [`atreplinit`](@ref)를 사용하세요:

```julia
atreplinit() do repl
    # ...
end
```

## [Command-line switches for Julia](@id command-line-interface)

Julia 코드를 실행하고 `perl` 및 `ruby` 프로그램에서 사용할 수 있는 것과 유사한 옵션을 제공하는 다양한 방법이 있습니다:

```
julia [switches] -- [programfile] [args...]
```

다음은 julia를 실행할 때 사용할 수 있는 명령줄 스위치의 전체 목록입니다 (*는 기본값을 나타내며, '($)'로 표시된 설정은 패키지 사전 컴파일을 트리거할 수 있습니다):

| Switch                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------------------------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-v`, `--version`                                 | Display version information                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-h`, `--help`                                    | Print command-line options (this message)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `--help-hidden`                                   | Print uncommon options not shown by `-h`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `--project[={<dir>\|@.}]`                         | Set `<dir>` as the active project/environment. The default `@.` option will search through parent directories until a `Project.toml` or `JuliaProject.toml` file is found.                                                                                                                                                                                                                                                                                                                                                                                    |
| `-J`, `--sysimage <file>`                         | Start up with the given system image file                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-H`, `--home <dir>`                              | Set location of `julia` executable                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `--startup-file={yes*\|no}`                       | Load `JULIA_DEPOT_PATH/config/startup.jl`; if [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) environment variable is unset, load `~/.julia/config/startup.jl`                                                                                                                                                                                                                                                                                                                                                                                                    |
| `--handle-signals={yes*\|no}`                     | Enable or disable Julia's default signal handlers                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `--sysimage-native-code={yes*\|no}`               | Use native code from system image if available                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `--compiled-modules={yes*\|no\|existing\|strict}` | Enable or disable incremental precompilation of modules. The `existing` option allows use of existing compiled modules that were previously precompiled, but disallows creation of new precompile files. The `strict` option is similar, but will error if no precompile file is found.                                                                                                                                                                                                                                                                       |
| `--pkgimages={yes*\|no\|existing}`                | Enable or disable usage of native code caching in the form of pkgimages. The `existing` option allows use of existing pkgimages but disallows creation of new ones                                                                                                                                                                                                                                                                                                                                                                                            |
| `-e`, `--eval <expr>`                             | Evaluate `<expr>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-E`, `--print <expr>`                            | Evaluate `<expr>` and display the result                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-m`, `--module <Package> [args]`                 | Run entry point of `Package` (`@main` function) with `args'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-L`, `--load <file>`                             | Load `<file>` immediately on all processors                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-t`, `--threads {auto\|N[,auto\|M]}`             | Enable N[+M] threads; N threads are assigned to the `default` threadpool, and if M is specified, M threads are assigned to the `interactive` threadpool; `auto` tries to infer a useful default number of threads to use but the exact behavior might change in the future. Currently sets N to the number of CPUs assigned to this Julia process based on the OS-specific affinity assignment interface if supported (Linux and Windows) or to the number of CPU threads if not supported (MacOS) or if process affinity is not configured, and sets M to 1. |
| `--gcthreads=N[,M]`                               | Use N threads for the mark phase of GC and M (0 or 1) threads for the concurrent sweeping phase of GC. N is set to half of the number of compute threads and M is set to 0 if unspecified.                                                                                                                                                                                                                                                                                                                                                                    |
| `-p`, `--procs {N\|auto}`                         | Integer value N launches N additional local worker processes; `auto` launches as many workers as the number of local CPU threads (logical cores)                                                                                                                                                                                                                                                                                                                                                                                                              |
| `--machine-file <file>`                           | Run processes on hosts listed in `<file>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-i`, `--interactive`                             | Interactive mode; REPL runs and `isinteractive()` is true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-q`, `--quiet`                                   | Quiet startup: no banner, suppress REPL warnings                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `--banner={yes\|no\|short\|auto*}`                | Enable or disable startup banner                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `--color={yes\|no\|auto*}`                        | Enable or disable color text                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `--history-file={yes*\|no}`                       | Load or save history                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `--depwarn={yes\|no*\|error}`                     | Enable or disable syntax and method deprecation warnings (`error` turns warnings into errors)                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `--warn-overwrite={yes\|no*}`                     | Enable or disable method overwrite warnings                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `--warn-scope={yes*\|no}`                         | Enable or disable warning for ambiguous top-level scope                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-C`, `--cpu-target <target>`                     | Limit usage of CPU features up to `<target>`; set to `help` to see the available options                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-O`, `--optimize={0\|1\|2*\|3}`                  | Set the optimization level (level is 3 if `-O` is used without a level) ($)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `--min-optlevel={0*\|1\|2\|3}`                    | Set the lower bound on per-module optimization                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-g`, `--debug-info={0\|1*\|2}`                   | Set the level of debug info generation (level is 2 if `-g` is used without a level) ($)                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `--inline={yes\|no}`                              | Control whether inlining is permitted, including overriding `@inline` declarations                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `--check-bounds={yes\|no\|auto*}`                 | Emit bounds checks always, never, or respect `@inbounds` declarations ($)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `--math-mode={ieee,fast}`                         | Disallow or enable unsafe floating point optimizations (overrides `@fastmath` declaration)                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `--polly={yes*\|no}`                              | Enable or disable the polyhedral optimizer Polly (overrides @polly declaration)                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `--code-coverage[={none*\|user\|all}]`            | Count executions of source lines (omitting setting is equivalent to `user`)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `--code-coverage=@<path>`                         | Count executions but only in files that fall under the given file path/directory. The `@` prefix is required to select this option. A `@` with no path will track the current directory.                                                                                                                                                                                                                                                                                                                                                                      |
| `--code-coverage=tracefile.info`                  | Append coverage information to the LCOV tracefile (filename supports format tokens).                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `--track-allocation[={none*\|user\|all}]`         | Count bytes allocated by each source line (omitting setting is equivalent to "user")                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `--track-allocation=@<path>`                      | Count bytes but only in files that fall under the given file path/directory. The `@` prefix is required to select this option. A `@` with no path will track the current directory.                                                                                                                                                                                                                                                                                                                                                                           |
| `--bug-report=KIND`                               | Launch a bug report session. It can be used to start a REPL, run a script, or evaluate expressions. It first tries to use BugReporting.jl installed in current environment and falls back to the latest compatible BugReporting.jl if not. For more information, see `--bug-report=help`.                                                                                                                                                                                                                                                                     |
| `--heap-size-hint=<size>`                         | Forces garbage collection if memory usage is higher than the given value. The value may be specified as a number of bytes, optionally in units of KB, MB, GB, or TB, or as a percentage of physical memory with %.                                                                                                                                                                                                                                                                                                                                            |
| `--compile={yes*\|no\|all\|min}`                  | Enable or disable JIT compiler, or request exhaustive or minimal compilation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `--output-o <name>`                               | Generate an object file (including system image data)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `--output-ji <name>`                              | Generate a system image data file (.ji)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `--strip-metadata`                                | Remove docstrings and source location info from system image                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `--strip-ir`                                      | Remove IR (intermediate representation) of compiled functions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `--output-unopt-bc <name>`                        | Generate unoptimized LLVM bitcode (.bc)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `--output-bc <name>`                              | Generate LLVM bitcode (.bc)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `--output-asm <name>`                             | Generate an assembly file (.s)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `--output-incremental={yes\|no*}`                 | Generate an incremental output file (rather than complete)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `--trace-compile={stderr\|name}`                  | Print precompile statements for methods compiled during execution or save to a path                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `--image-codegen`                                 | Force generate code in imaging mode                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `--permalloc-pkgimg={yes\|no*}`                   | Copy the data section of package images into memory                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

!!! compat "Julia 1.1"
    줄리아 1.0에서는 기본 `--project=@.` 옵션이 Git 저장소의 루트 디렉토리에서 `Project.toml` 파일을 검색하지 않았습니다. 줄리아 1.1부터는 검색합니다.

