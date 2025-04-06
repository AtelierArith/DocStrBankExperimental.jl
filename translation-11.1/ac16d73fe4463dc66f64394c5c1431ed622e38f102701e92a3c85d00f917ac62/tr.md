# Running External Programs

Julia, shell, Perl ve Ruby'den komutlar için backtick notasyonunu ödünç alır. Ancak, Julia'da yazmak

```jldoctest
julia> `echo hello`
`echo hello`
```

çeşitli kabuklar, Perl veya Ruby'deki davranışlardan birkaç açıdan farklıdır:

  * Bunun yerine komutu hemen çalıştırmak yerine, backtick'ler bir [`Cmd`](@ref) nesnesi oluşturur ve bu nesne komutu diğerleriyle borular aracılığıyla bağlamak için kullanılabilir, [`run`](@ref) onu ve [`read`](@ref) veya [`write`](@ref) ona bağlamak için.
  * Komut çalıştırıldığında, Julia çıktısını yakalamaz, eğer bunu özel olarak ayarlamazsanız. Bunun yerine, komutun çıktısı varsayılan olarak [`stdout`](@ref)'ya gider; bu, `libc`'nin `system` çağrısını kullanıyormuş gibi.
  * Komut asla bir kabukla çalıştırılmaz. Bunun yerine, Julia komut sözdizimini doğrudan ayrıştırır, değişkenleri uygun şekilde içe aktarır ve kabuğun yaptığı gibi kelimelere ayırır, kabuk alıntı sözdizimini dikkate alır. Komut, `julia`'nın doğrudan çocuk süreci olarak çalıştırılır ve `fork` ve `exec` çağrıları kullanılır.

!!! note
    Aşağıdakiler, Linux veya MacOS'taki gibi bir Posix ortamını varsayar. Windows'ta, `echo` ve `dir` gibi birçok benzer komut, harici programlar değil, bunun yerine `cmd.exe` kabuğunun kendisine entegre edilmiştir. Bu komutları çalıştırmanın bir yolu, `cmd.exe`'yi çağırmaktır; örneğin `cmd /C echo hello`. Alternatif olarak, Julia, Cygwin gibi bir Posix ortamında çalıştırılabilir.


İşte bir dış programı çalıştırmanın basit bir örneği:

```jldoctest
julia> mycommand = `echo hello`
`echo hello`

julia> typeof(mycommand)
Cmd

julia> run(mycommand);
hello
```

`hello` `echo` komutunun çıktısıdır, [`stdout`](@ref)'ya gönderilmiştir. Dış komut başarılı bir şekilde çalışmazsa, run metodu [`ProcessFailedException`](@ref) hatasını fırlatır.

Eğer dış komutun çıktısını okumak istiyorsanız, [`read`](@ref) veya [`readchomp`](@ref) yerine kullanılabilir:

```jldoctest
julia> read(`echo hello`, String)
"hello\n"

julia> readchomp(`echo hello`)
"hello"
```

Daha genel olarak, [`open`](@ref) dış bir komuttan okumak veya yazmak için kullanılabilir.

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

Program adı ve bir komuttaki bireysel argümanlar, komut bir dizi dizeymiş gibi erişilip döngüye alınabilir:

```jldoctest
julia> collect(`echo "foo bar"`)
2-element Vector{String}:
 "echo"
 "foo bar"

julia> `echo "foo bar"`[2]
"foo bar"
```

## [Interpolation](@id command-interpolation)

Diyelim ki biraz daha karmaşık bir şey yapmak istiyorsunuz ve bir dosyanın adını `file` değişkeninde bir komutun argümanı olarak kullanmak istiyorsunuz. `$` işaretini, bir dize literali gibi interpolasyon için kullanabilirsiniz (bkz. [Strings](@ref)):

```jldoctest
julia> file = "/etc/passwd"
"/etc/passwd"

julia> `sort $file`
`sort /etc/passwd`
```

Bir shell aracılığıyla dış programlar çalıştırırken yaygın bir tuzak, bir dosya adının shell için özel olan karakterler içermesi durumunda istenmeyen davranışlara neden olabilmesidir. Örneğin, `/etc/passwd` yerine `/Volumes/External HD/data.csv` dosyasının içeriğini sıralamak isteseydik. Hadi deneyelim:

```jldoctest
julia> file = "/Volumes/External HD/data.csv"
"/Volumes/External HD/data.csv"

julia> `sort $file`
`sort '/Volumes/External HD/data.csv'`
```

Dosya adı nasıl alıntılandı? Julia, `file`'ın tek bir argüman olarak yerleştirileceğini bildiği için kelimeyi sizin için alıntılar. Aslında, bu tam olarak doğru değil: `file`'ın değeri asla bir kabuk tarafından yorumlanmaz, bu nedenle gerçek alıntılamaya gerek yoktur; alıntılar yalnızca kullanıcıya sunum için eklenir. Bu, bir değeri bir kabuk kelimesinin parçası olarak yerleştirirseniz bile çalışacaktır:

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

Gördüğünüz gibi, `path` değişkenindeki boşluk uygun şekilde kaçırılmış. Ama ya birden fazla kelimeyi *birleştirmek* isterseniz? Bu durumda, sadece bir dizi (veya başka bir yineleyici konteyner) kullanın:

```jldoctest
julia> files = ["/etc/passwd","/Volumes/External HD/data.csv"]
2-element Vector{String}:
 "/etc/passwd"
 "/Volumes/External HD/data.csv"

julia> `grep foo $files`
`grep foo /etc/passwd '/Volumes/External HD/data.csv'`
```

Eğer bir diziyi bir shell kelimesinin parçası olarak iç içe geçirirseniz, Julia shell'in `{a,b,c}` argüman üretimini taklit eder:

```jldoctest
julia> names = ["foo","bar","baz"]
3-element Vector{String}:
 "foo"
 "bar"
 "baz"

julia> `grep xylophone $names.txt`
`grep xylophone foo.txt bar.txt baz.txt`
```

Ayrıca, birden fazla diziyi aynı kelimeye iç içe geçirirseniz, kabuğun Kartezyen çarpım üretim davranışı taklit edilir:

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

Geçici dizi nesneleri oluşturmaya gerek kalmadan, bu üretken işlevselliği kullanabilirsiniz çünkü literal dizileri iç içe geçirebilirsiniz:

```jldoctest
julia> `rm -rf $["foo","bar","baz","qux"].$["aux","log","pdf"]`
`rm -rf foo.aux foo.log foo.pdf bar.aux bar.log bar.pdf baz.aux baz.log baz.pdf qux.aux qux.log qux.pdf`
```

## Quoting

Kaçınılmaz olarak, birinin o kadar basit olmayan komutlar yazmak istemesi ve alıntı kullanmanın gerekli hale gelmesi. İşte bir shell istemcisinde basit bir Perl tek satırlık örnek:

```
sh$ perl -le '$|=1; for (0..3) { print }'
0
1
2
3
```

Perl ifadesinin iki nedenle tek tırnak içinde olması gerekir: böylece boşluklar ifadenin birden fazla shell kelimesine bölünmesini engeller ve `$|` gibi Perl değişkenlerinin (evet, bu bir Perl değişkeninin adı) interpolasyona neden olmasını engeller. Diğer durumlarda, interpolasyonun *gerçekleşmesini* sağlamak için çift tırnak kullanmak isteyebilirsiniz:

```
sh$ first="A"
sh$ second="B"
sh$ perl -le '$|=1; print for @ARGV' "1: $first" "2: $second"
1: A
2: B
```

Genel olarak, Julia backtick sözdizimi, shell komutlarını olduğu gibi backtick içine kesip yapıştırabilmeniz için dikkatlice tasarlanmıştır ve bunlar çalışacaktır: kaçış, alıntılama ve yerleştirme davranışları shell ile aynıdır. Tek fark, yerleştirmenin entegre edilmesi ve Julia'nın tek bir dize değeri ile birden fazla değer için bir konteynerin ne olduğunu bilmesidir. Yukarıdaki iki örneği Julia'da deneyelim:

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

Sonuçlar aynıdır ve Julia'nın ara yüz davranışı, bazı iyileştirmelerle birlikte shell'in davranışını taklit eder; çünkü Julia, çoğu shell'in bu amaçla boşluklara göre böldüğü dizgelerin yerine birinci sınıf yineleyici nesneleri destekler, bu da belirsizlikler yaratır. Shell komutlarını Julia'ya taşımaya çalışırken, önce kesip yapıştırmayı deneyin. Julia, komutları çalıştırmadan önce size gösterdiğinden, yorumunu kolayca ve güvenli bir şekilde inceleyebilir, herhangi bir zarar vermeden.

## Pipelines

Shell metakarakterleri, `|`, `&` ve `>`, Julia'nın ters tırnakları içinde alıntılanmalı (veya kaçırılmalıdır):

```jldoctest
julia> run(`echo hello '|' sort`);
hello | sort

julia> run(`echo hello \| sort`);
hello | sort
```

Bu ifade, `echo` komutunu `hello`, `|` ve `sort` olarak üç kelime ile argüman olarak çağırır. Sonuç olarak, tek bir satır yazdırılır: `hello | sort`. Peki, o zaman bir boru hattı nasıl oluşturulur? Ters tırnaklar içinde `'|'` kullanmak yerine, [`pipeline`](@ref) kullanılır:

```jldoctest
julia> run(pipeline(`echo hello`, `sort`));
hello
```

Bu, `echo` komutunun çıktısını `sort` komutuna yönlendirir. Elbette, sıralanacak yalnızca bir satır olduğu için bu pek ilginç değil, ancak kesinlikle çok daha ilginç şeyler yapabiliriz:

```julia-repl
julia> run(pipeline(`cut -d: -f3 /etc/passwd`, `sort -n`, `tail -n5`))
210
211
212
213
214
```

Bu, bir UNIX sisteminde en yüksek beş kullanıcı kimliğini yazdırır. `cut`, `sort` ve `tail` komutları, mevcut `julia` sürecinin hemen çocukları olarak başlatılır ve arada bir kabuk süreci yoktur. Julia, boruları ayarlamak ve genellikle kabuk tarafından yapılan dosya tanımlayıcılarını bağlamak için gereken işlemleri kendisi yapar. Julia bunu kendisi yaptığı için daha iyi kontrol sağlar ve kabukların yapamadığı bazı şeyleri yapabilir.

Julia birden fazla komutu paralel olarak çalıştırabilir:

```jldoctest; filter = r"(world\nhello|hello\nworld)"
julia> run(`echo hello` & `echo world`);
world
hello
```

Çıktının sırası burada belirsizdir çünkü iki `echo` süreci neredeyse aynı anda başlatılır ve birbirleriyle ve `julia` ana süreciyle paylaştıkları [`stdout`](@ref) tanımlayıcısına ilk yazma için yarışırlar. Julia, bu iki sürecin çıktısını başka bir programa yönlendirmeye izin verir:

```jldoctest
julia> run(pipeline(`echo world` & `echo hello`, `sort`));
hello
world
```

UNIX sıhhi tesisatında burada olan, tek bir UNIX boru nesnesinin oluşturulması ve her iki `echo` işlemi tarafından yazılmasıdır; borunun diğer ucu ise `sort` komutu tarafından okunmaktadır.

IO yönlendirmesi, `pipeline` fonksiyonuna `stdin`, `stdout` ve `stderr` anahtar kelime argümanlarını geçirerek gerçekleştirilebilir:

```julia
pipeline(`do_work`, stdout=pipeline(`sort`, "out.txt"), stderr="errs.txt")
```

### Avoiding Deadlock in Pipelines

Bir işlemden bir borunun her iki ucuna okuma ve yazma yaparken, çekirdeği tüm verileri tamponlamaya zorlamaktan kaçınmak önemlidir.

Örneğin, bir komutun tüm çıktısını okurken `read(out, String)` çağrısını yapın, `wait(process)` değil, çünkü ilki, süreç tarafından yazılan tüm verileri aktif olarak tüketecektir, oysa ikincisi, bir okuyucunun bağlanmasını beklerken verileri çekirdek tamponlarında depolamaya çalışacaktır.

Başka bir yaygın çözüm, boru hattının okuyucusunu ve yazarını ayrı [`Task`](@ref)'lara ayırmaktır:

```julia
writer = @async write(process, "data")
reader = @async do_compute(read(process, String))
wait(writer)
fetch(reader)
```

(aynı zamanda okuyucu ayrı bir görev değildir, çünkü hemen `fetch` ediyoruz zaten).

### Complex Example

Yüksek seviyeli bir programlama dili, birinci sınıf bir komut soyutlaması ve süreçler arasında otomatik boru hattı kurulumu kombinasyonu güçlü bir yapıdır. Kolayca oluşturulabilen karmaşık boru hatlarına dair bir fikir vermek için, işte bazı daha sofistike örnekler; Perl tek satırlarının aşırı kullanımından dolayı özür dilerim:

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

Bu, iki eşzamanlı tüketiciye tek bir üreticinin beslediği klasik bir örnektir: bir `perl` süreci, üzerinde 0'dan 5'e kadar sayılar bulunan satırlar üretirken, iki paralel süreç bu çıktıyı tüketir; biri satırları "A" harfi ile, diğeri "B" harfi ile öne ekler. İlk satırı hangi tüketicinin alacağı belirsizdir, ancak bu yarış kazanıldıktan sonra, satırlar bir süreç tarafından ve ardından diğer süreç tarafından sırayla tüketilir. (Perl'de `$|=1` ayarı, her print ifadesinin [`stdout`](@ref) tanıtıcısını boşaltmasını sağlar; bu, bu örneğin çalışması için gereklidir. Aksi takdirde, tüm çıktı tamponlanır ve bir kerede boruya yazılır, bu da yalnızca bir tüketici süreci tarafından okunur.)

İşte daha karmaşık bir çok aşamalı üretici-tüketici örneği:

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

Bu örnek, önceki örneğe benzer, ancak iki aşamalı tüketiciler vardır ve aşamalar farklı gecikmelere sahip olduğu için doygun verimliliği korumak amacıyla farklı sayıda paralel işçi kullanırlar.

Bu örneklerin hepsini denemenizi şiddetle tavsiye ederiz, böylece nasıl çalıştıklarını görebilirsiniz.

## `Cmd` Objects

[`Cmd`](@ref) türünde bir nesne oluşturmak için backtick sözdizimi kullanılır. Böyle bir nesne, mevcut bir `Cmd` veya argümanlar listesinden de doğrudan oluşturulabilir:

```julia
run(Cmd(`pwd`, dir=".."))
run(Cmd(["pwd"], detach=true, ignorestatus=true))
```

Bu, `Cmd`'nin yürütme ortamının çeşitli yönlerini anahtar kelime argümanları aracılığıyla belirtmenizi sağlar. Örneğin, `dir` anahtar kelimesi `Cmd`'nin çalışma dizini üzerinde kontrol sağlar:

```jldoctest
julia> run(Cmd(`pwd`, dir="/"));
/
```

Ve `env` anahtar kelimesi, yürütme ortamı değişkenlerini ayarlamanıza olanak tanır:

```jldoctest
julia> run(Cmd(`sh -c "echo foo \$HOWLONG"`, env=("HOWLONG" => "ever!",)));
foo ever!
```

[`Cmd`](@ref) için ek anahtar argümanlarına bakın. [`setenv`](@ref) ve [`addenv`](@ref) komutları, sırasıyla `Cmd` yürütme ortam değişkenlerini değiştirmek veya eklemek için başka bir yol sağlar:

```jldoctest
julia> run(setenv(`sh -c "echo foo \$HOWLONG"`, ("HOWLONG" => "ever!",)));
foo ever!

julia> run(addenv(`sh -c "echo foo \$HOWLONG"`, "HOWLONG" => "ever!"));
foo ever!
```
