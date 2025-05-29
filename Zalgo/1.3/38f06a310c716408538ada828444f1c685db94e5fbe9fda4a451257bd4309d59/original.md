```
zalgo(str::String, upmarks = 1:4, middlemarks = 1:4,
    downmarks = 1:4, maxmarks = 6)
```

Randomly add up to `maxmarks` diacritic marks to each letter of `str`. The `upmarks`, `middlemarks`, and `downmarks` ranges determine the minimum and maximum number of diacritic marks added to the letter at that position.
