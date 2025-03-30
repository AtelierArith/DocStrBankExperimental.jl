```
bind(chnl::Channel, task::Task)
```

`chnl`'nin ömrünü bir görevle ilişkilendirir. `Channel` `chnl`, görev sona erdiğinde otomatik olarak kapatılır. Görevde yakalanmamış herhangi bir istisna, `chnl` üzerindeki tüm bekleyenlere iletilir.

`chnl` nesnesi, görev sona ermesinden bağımsız olarak açıkça kapatılabilir. Sona eren görevler, zaten kapatılmış `Channel` nesneleri üzerinde hiçbir etkiye sahip değildir.

Bir kanal birden fazla göreve bağlandığında, ilk sona eren görev kanalı kapatır. Aynı göreve bağlı birden fazla kanal olduğunda, görevin sona ermesi tüm bağlı kanalları kapatır.

# Örnekler

```jldoctest
julia> c = Channel(0);

julia> task = @async foreach(i->put!(c, i), 1:4);

julia> bind(c,task);

julia> for i in c
           @show i
       end;
i = 1
i = 2
i = 3
i = 4

julia> isopen(c)
false
```

```jldoctest
julia> c = Channel(0);

julia> task = @async (put!(c, 1); error("foo"));

julia> bind(c, task);

julia> take!(c)
1

julia> put!(c, 1);
HATA: TaskFailedException
Stacktrace:
[...]
    nested task error: foo
[...]
```
