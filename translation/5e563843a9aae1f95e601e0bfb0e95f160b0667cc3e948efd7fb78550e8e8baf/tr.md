```
Threads.atomic_fence()
```

Sıralı tutarlılık bellek engeli ekleyin

Sıralı tutarlılık sıralama anlamsalara sahip bir bellek engeli ekler. Bunun gerekli olduğu, yani bir edinme/salım sıralamasının yetersiz olduğu algoritmalar vardır.

Bu muhtemelen çok pahalı bir işlemdir. Julia'daki diğer tüm atomik işlemlerin zaten edinme/salım anlamsalara sahip olduğu göz önüne alındığında, açık engeller çoğu durumda gerekli olmamalıdır.

Daha fazla ayrıntı için, LLVM'nin `fence` talimatına bakın.
