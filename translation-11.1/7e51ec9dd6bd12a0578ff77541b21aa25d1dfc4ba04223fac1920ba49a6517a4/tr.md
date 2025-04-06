```
@arg_test arg1 arg2 ... body
```

`@arg_test` makrosu, `arg_readers` ve `arg_writers` tarafından sağlanan `arg` fonksiyonlarını gerçek argüman değerlerine dönüştürmek için kullanılır. `@arg_test arg body` yazdığınızda, bu `arg(arg -> body)` ile eşdeğerdir.
