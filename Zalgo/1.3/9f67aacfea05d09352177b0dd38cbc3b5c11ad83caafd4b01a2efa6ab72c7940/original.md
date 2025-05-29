Zalgo.jl does two things.

  * It adds pointless diacritics to text: `zalgo("Cthulhu")`
  * It converts an input ASCII string to equivalent characters found in the darkest recesses of the Unicode charts:

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

`large_type("Hello World")` displays the text using the Large Type glyphs added to Unicode in version 16.
