# [Command-line Interface](@id cli)

## Using arguments inside scripts

Bir `julia` betiği çalıştırırken, betiğinize ek argümanlar geçebilirsiniz:

```
$ julia script.jl arg1 arg2...
```

Bu ek komut satırı argümanları, global sabit `ARGS` içinde geçilir. Script'in adı ise global `PROGRAM_FILE` olarak geçilir. `ARGS`'ın, komut satırında `-e` seçeneği kullanılarak bir Julia ifadesi verildiğinde de ayarlandığını unutmayın (aşağıdaki `julia` yardım çıktısına bakın) ancak `PROGRAM_FILE` boş olacaktır. Örneğin, bir script'e verilen argümanları sadece yazdırmak için bunu yapabilirsiniz:

```
$ julia -e 'println(PROGRAM_FILE); for x in ARGS; println(x); end' foo bar

foo
bar
```

Ya da o kodu bir betiğe koyup çalıştırabilirsin:

```
$ echo 'println(PROGRAM_FILE); for x in ARGS; println(x); end' > script.jl
$ julia script.jl foo bar
script.jl
foo
bar
```

`--` ayırıcı, komut satırı argümanlarını script dosyası için olanlardan ve Julia için olanlardan ayırmak için kullanılabilir:

```
$ julia --color=yes -O -- script.jl arg1 arg2..
```

Ayrıca daha fazla bilgi için [Scripting](@ref man-scripting)'e bakın.

## The `Main.main` entry point

Julia 1.11 itibarıyla, `Base` makro `@main`'i dışa aktarmaktadır. Bu makro, `main` sembolüne genişler, ancak bir betiğin veya ifadenin yürütülmesinin sonunda, `julia` böyle bir fonksiyon tanımlanmışsa ve bu davranış `@main` makrosu kullanılarak tercih edilmişse, `Main.main(ARGS)` fonksiyonunu yürütmeye çalışacaktır.

Bu özellik, derlenmiş ve etkileşimli iş akışlarının birleştirilmesine yardımcı olmayı amaçlamaktadır. Derlenmiş iş akışlarında, `main` fonksiyonunu tanımlayan kodun yüklenmesi, çağrısından mekansal ve zamansal olarak ayrılmış olabilir. Ancak, etkileşimli iş akışları için davranış, değerlendirilen betiğin veya ifadenin sonunda `exit(main(ARGS))` çağrısını açıkça yapmakla eşdeğerdir.

!!! compat "Julia 1.11"
    Özel giriş noktası `Main.main`, Julia 1.11'de eklendi. Önceki Julia sürümleriyle uyumluluk için, betiklerinizin sonuna açık bir `@isdefined(var"@main") ? (@main) : exit(main(ARGS))` ekleyin.


Bu özelliği eylemde görmek için, `main`'e açık bir çağrı olmamasına rağmen print fonksiyonunu çalıştıracak olan aşağıdaki tanıma bakın:

```
$ julia -e '(@main)(args) = println("Hello World!")'
Hello World!
$
```

Sadece `Main` modülündeki `main` bağlaması bu davranışa sahiptir ve yalnızca `@main` makrosu tanımlayıcı modül içinde kullanıldıysa.

Örneğin, `main` yerine `hello` kullanmak `hello` fonksiyonunun çalışmasına neden olmayacaktır:

```
$ julia -e 'hello(ARGS) = println("Hello World!")'
$
```

ve ne de `main`'in sade bir tanımı:

```
$ julia -e 'main(ARGS) = println("Hello World!")'
$
```

Ancak, opt-in tanım zamanında gerçekleşmek zorunda değildir:

```
$ julia -e 'main(ARGS) = println("Hello World!"); @main'
Hello World!
$
```

`main` bağlamı bir paketten içe aktarılabilir. Aşağıda tanımlanan bir *merhaba dünya* paketi

```
module Hello

export main
(@main)(args) = println("Hello from the package!")

end
```

şu şekilde kullanılabilir:

```
$ julia -e 'using Hello'
Hello from the package!
$ julia -e 'import Hello' # N.B.: Execution depends on the binding not whether the package is loaded
$
```

Ancak, mevcut en iyi uygulama önerisinin, uygulama ve yeniden kullanılabilir kütüphane kodunu aynı pakette karıştırmamak olduğu unutulmamalıdır. Yardımcı uygulamalar, ayrı paketler olarak veya bir paketin `bin` klasöründeki ayrı `main` giriş noktalarıyla betikler olarak dağıtılabilir.

## Parallel mode

Julia, `-p` veya `--machine-file` seçenekleri ile paralel modda başlatılabilir. `-p n`, ek `n` işçi süreci başlatırken, `--machine-file file`, `file` dosyasındaki her satır için bir işçi başlatır. `file` dosyasında tanımlanan makineler, şifresiz `ssh` girişi ile erişilebilir olmalı ve Julia, mevcut ana bilgisayarla aynı konumda kurulu olmalıdır. Her makine tanımı `[count*][user@]host[:port] [bind_addr[:port]]` biçimindedir. `user`, mevcut kullanıcıya, `port` ise standart ssh portuna varsayılan olarak ayarlanır. `count`, düğümde başlatılacak işçi sayısıdır ve varsayılan olarak 1'dir. İsteğe bağlı `bind-to bind_addr[:port]`, diğer işçilerin bu işçiye bağlanmak için kullanması gereken IP adresi ve portu belirtir.

## Startup file

Eğer Julia çalıştırıldığında yürütülmesini istediğiniz bir kodunuz varsa, bunu `~/.julia/config/startup.jl` dosyasına koyabilirsiniz:

```
$ echo 'println("Greetings! 你好! 안녕하세요?")' > ~/.julia/config/startup.jl
$ julia
Greetings! 你好! 안녕하세요?

...
```

Not edin ki, Julia'yı ilk kez çalıştırdıktan sonra `~/.julia` dizinine sahip olmanız gerekir, ancak bunu kullanıyorsanız `~/.julia/config` klasörünü ve `~/.julia/config/startup.jl` dosyasını oluşturmanız gerekebilir.

[The Julia REPL](@ref) içinde yalnızca başlangıç kodunun çalışmasını sağlamak için (ve `julia` bir betik üzerinde çalıştırıldığında değil), [`atreplinit`](@ref)'yı `startup.jl` içinde kullanın:

```julia
atreplinit() do repl
    # ...
end
```

## [Command-line switches for Julia](@id command-line-interface)

Julia kodunu çalıştırmanın ve `perl` ve `ruby` programlarına benzer seçenekler sunmanın çeşitli yolları vardır:

```
julia [switches] -- [programfile] [args...]
```

Aşağıda julia başlatıldığında mevcut olan komut satırı anahtarlarının tam listesi bulunmaktadır (bir '*' varsayılan değeri işaret eder, eğer uygulanabilir ise; '($)' ile işaretlenmiş ayarlar paket ön derlemesini tetikleyebilir):

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
    Julia 1.0'da varsayılan `--project=@.` seçeneği, bir Git deposunun kök dizininden `Project.toml` dosyasını aramıyordu. Julia 1.1'den itibaren, bunu yapmaktadır.

