# Inference

## How inference works

Julia derleyicisinde, "tip çıkarımı", giriş değerlerinin türlerinden sonraki değerlerin türlerini çıkarma sürecini ifade eder. Julia'nın çıkarım yaklaşımı aşağıdaki blog yazılarında tanımlanmıştır:

1. [Shows a simplified implementation of the data-flow analysis algorithm, that Julia's type inference routine is based on.](https://aviatesk.github.io/posts/data-flow-problem/)
2. [Gives a high level view of inference with a focus on its inter-procedural convergence guarantee.](https://info.juliahub.com/inference-convergence-algorithm-in-julia)
3. [Explains a refinement on the algorithm introduced in 2.](https://info.juliahub.com/inference-convergence-algorithm-in-julia-revisited)

## Debugging compiler.jl

Julia oturumunu başlatabilir, `compiler/*.jl` dosyalarını düzenleyebilir (örneğin `print` ifadeleri eklemek için) ve ardından çalışan oturumunuzda `Core.Compiler`'ı değiştirmek için `base` dizinine gidip `include("compiler/compiler.jl")` komutunu çalıştırabilirsiniz. Bu hile, her değişiklik için Julia'yı yeniden derlemekten çok daha hızlı bir geliştirme sürecine genellikle yol açar.

Alternatif olarak, derleyici değişikliklerini takip etmek için [Revise.jl](https://github.com/timholy/Revise.jl) paketini kullanabilirsiniz. Julia oturumunuzun başında `Revise.track(Core.Compiler)` komutunu kullanarak bunu yapabilirsiniz. [Revise documentation](https://timholy.github.io/Revise.jl/stable/) adresinde açıklandığı gibi, derleyicideki değişiklikler, değiştirilmiş dosyalar kaydedildiğinde yansıyacaktır.

Bir çıkarım için uygun bir giriş noktası `typeinf_code`'dır. İşte `convert(Int, UInt(1))` üzerinde çıkarım yapmayı gösteren bir demo:

```julia
# Get the method
atypes = Tuple{Type{Int}, UInt}  # argument types
mths = methods(convert, atypes)  # worth checking that there is only one
m = first(mths)

# Create variables needed to call `typeinf_code`
interp = Core.Compiler.NativeInterpreter()
sparams = Core.svec()      # this particular method doesn't have type-parameters
run_optimizer = true       # run all inference optimizations
types = Tuple{typeof(convert), atypes.parameters...} # Tuple{typeof(convert), Type{Int}, UInt}
Core.Compiler.typeinf_code(interp, m, types, sparams, run_optimizer)
```

Eğer hata ayıklama maceralarınız bir `MethodInstance` gerektiriyorsa, yukarıdaki birçok değişkeni kullanarak `Core.Compiler.specialize_method` çağrısı yaparak onu bulabilirsiniz. Bir `CodeInfo` nesnesi elde edilebilir.

```julia
# Returns the CodeInfo object for `convert(Int, ::UInt)`:
ci = (@code_typed convert(Int, UInt(1)))[1]
```

## The inlining algorithm (`inline_worthy`)

Inline çalışmasının en zor kısmı `ssa_inlining_pass!` içinde gerçekleşir. Ancak, "fonksiyonum neden inline olmadı?" sorusuyla ilgileniyorsanız, muhtemelen fonksiyon çağrısını inline yapma kararını veren `inline_worthy` ile ilgileneceksiniz.

`inline_worthy` implements a cost-model, where "cheap" functions get inlined; more specifically, we inline functions if their anticipated run-time is not large compared to the time it would take to [issue a call](https://en.wikipedia.org/wiki/Calling_convention) to them if they were not inlined. The cost-model is extremely simple and ignores many important details: for example, all `for` loops are analyzed as if they will be executed once, and the cost of an `if...else...end` includes the summed cost of all branches. It's also worth acknowledging that we currently lack a suite of functions suitable for testing how well the cost model predicts the actual run-time cost, although [BaseBenchmarks](https://github.com/JuliaCI/BaseBenchmarks.jl) provides a great deal of indirect information about the successes and failures of any modification to the inlining algorithm.

Maliyet modelinin temeli, `add_tfunc` ve onun çağrıcılarında uygulanan bir arama tablosudur; bu tablo, Julia'nın yerleşik işlevlerinin her birine tahmini bir maliyet (CPU döngüleri cinsinden ölçülen) atar. Bu maliyetler, [standard ranges for common architectures](http://ithare.com/wp-content/uploads/part101_infographics_v08.png) (daha fazla ayrıntı için [Agner Fog's analysis](https://www.agner.org/optimize/instruction_tables.pdf)'ye bakın) temel alınarak belirlenmiştir.

Bu düşük seviyeli arama tablosunu bir dizi özel durumla tamamlıyoruz. Örneğin, tüm girdi ve çıktı türlerinin önceden çıkarıldığı bir `:invoke` ifadesi sabit bir maliyetle (şu anda 20 döngü) atanır. Buna karşılık, intrinsics/builtins dışındaki fonksiyonlar için bir `:call` ifadesi, çağrının dinamik yönlendirme gerektireceğini belirtir; bu durumda `Params.inline_nonleaf_penalty` tarafından belirlenen bir maliyet atanır (şu anda `1000` olarak ayarlanmıştır). Bunun, dinamik yönlendirmenin ham maliyetinin "ilk ilkeler" tahmini olmadığını, yalnızca dinamik yönlendirmenin son derece pahalı olduğunu belirten bir sezgi olduğunu unutmayın.

Her bir ifade, `statement_cost` adlı bir fonksiyonda toplam maliyeti için analiz edilir. Her ifadenin maliyetini aşağıdaki gibi görüntüleyebilirsiniz:

```jldoctest; filter=r"tuple.jl:\d+"
julia> Base.print_statement_costs(stdout, map, (typeof(sqrt), Tuple{Int},)) # map(sqrt, (2,))
map(f, t::Tuple{Any}) @ Base tuple.jl:281
  0 1 ─ %1  = $(Expr(:boundscheck, true))::Bool
  0 │   %2  = Base.getfield(_3, 1, %1)::Int64
  1 │   %3  = Base.sitofp(Float64, %2)::Float64
  0 │   %4  = Base.lt_float(%3, 0.0)::Bool
  0 └──       goto #3 if not %4
  0 2 ─       invoke Base.Math.throw_complex_domainerror(:sqrt::Symbol, %3::Float64)::Union{}
  0 └──       unreachable
 20 3 ─ %8  = Base.Math.sqrt_llvm(%3)::Float64
  0 └──       goto #4
  0 4 ─       goto #5
  0 5 ─ %11 = Core.tuple(%8)::Tuple{Float64}
  0 └──       return %11

```

Satır maliyetleri sol sütundadır. Bu, iç içe geçirme ve diğer optimizasyon biçimlerinin sonuçlarını içerir.
