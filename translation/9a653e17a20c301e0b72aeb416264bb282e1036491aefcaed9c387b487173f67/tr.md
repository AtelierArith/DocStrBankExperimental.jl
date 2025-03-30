```
@static
```

Bir ifadeyi analiz zamanı kısmen değerlendirin.

Örneğin, `@static Sys.iswindows() ? foo : bar` ifadesi `Sys.iswindows()`'u değerlendirir ve ifadeye ya `foo` ya da `bar` ekler. Bu, başka platformlarda geçersiz olacak bir yapının bulunduğu durumlarda yararlıdır, örneğin var olmayan bir işleve `ccall` yapmak gibi. `@static if Sys.isapple() foo end` ve `@static foo <&&,||> bar` da geçerli bir sözdizimidir.
