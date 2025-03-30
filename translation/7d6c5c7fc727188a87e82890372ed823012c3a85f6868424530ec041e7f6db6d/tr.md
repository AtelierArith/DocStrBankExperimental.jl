Bir [`Face`](@ref), metin görüntülemek için grafiksel özelliklerin bir koleksiyonudur. Yüzler, metnin terminalde ve muhtemelen diğer yerlerde nasıl görüntüleneceğini kontrol eder.

Çoğu zaman, bir [`Face`](@ref), *yüz adı* Symbol ile benzersiz bir ilişki olarak global yüzler sözlüklerinde saklanır ve genellikle bu isimle anılır, [`Face`](@ref) nesnesinin kendisi yerine.

# Özellikler

Tüm özellikler anahtar kelime yapıcı aracılığıyla ayarlanabilir ve varsayılan olarak `nothing` değerini alır.

  * `height` (bir `Int` veya `Float64`): Yükseklik, bir `Int` olduğunda desi-pt cinsinden veya bir `Float64` olduğunda temel boyutun bir faktörü olarak.
  * `weight` (bir `Symbol`): `:thin`, `:extralight`, `:light`, `:semilight`, `:normal`, `:medium`, `:semibold`, `:bold`, `:extrabold` veya `:black` sembollerinden biri (en hafiften en yoğun olana). Terminallerde, `:normal`dan daha büyük herhangi bir ağırlık kalın olarak görüntülenir ve değişken parlaklık metnini destekleyen terminallerde, `:normal`dan daha düşük herhangi bir ağırlık soluk olarak görüntülenir.
  * `slant` (bir `Symbol`): `:italic`, `:oblique` veya `:normal` sembollerinden biri.
  * `foreground` (bir `SimpleColor`): Metin ön plan rengi.
  * `background` (bir `SimpleColor`): Metin arka plan rengi.
  * `underline`, metin altı çizgisi, aşağıdaki formlardan birini alır:

      * bir `Bool`: Metnin altı çizili olup olmayacağı.
      * bir `SimpleColor`: Metin bu renkle altı çizili olmalıdır.
      * bir `Tuple{Nothing, Symbol}`: Metin, `:straight`, `:double`, `:curly`, `:dotted` veya `:dashed` sembolüyle belirlenen stil kullanılarak altı çizili olmalıdır.
      * bir `Tuple{SimpleColor, Symbol}`: Metin belirtilen SimpleColor ile altı çizili olmalı ve daha önce belirtilen sembol tarafından belirlenen stil kullanılmalıdır.
  * `strikethrough` (bir `Bool`): Metnin üstü çizili olup olmayacağı.
  * `inverse` (bir `Bool`): Ön plan ve arka plan renklerinin tersine çevrilip çevrilmeyeceği.
  * `inherit` (bir `Vector{Symbol}`): Öncelik sırasına göre miras alınacak yüzlerin isimleri. Tüm yüzler `:default` yüzünden miras alır.
