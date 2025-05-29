Zalgo.jlは2つのことを行います。

  * テキストに無意味なダイアクリティカルマークを追加します: `zalgo("Cthulhu")`
  * 入力されたASCII文字列をUnicodeチャートの最も暗い隅に見つかる同等の文字に変換します:

```
blackboard("Hello World")    
boldfraktur("Hello World")   
bolditalic("Hello World")    
bolditalicsans("Hello World")
boldroman("Hello World")     
boldsans("Hello World")      
boldscript("Hello World")    
boxed("hello world")         
circled("HELLO WORLD")       
fraktur("Hello World")       
italic("Hello World")        
italicsans("Hello World")    
sans("Hello World")          
script("Hello World")        
segmented("0123456789")      
teletype("Hello World")      
upsidedown("Hello World")    
```

`large_type("Hello World")`は、バージョン16でUnicodeに追加されたLarge Typeグリフを使用してテキストを表示します。
