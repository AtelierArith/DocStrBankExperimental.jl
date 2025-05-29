```
MovingWindow(desc, pre, after)
```

Constructs a `MovingWindow` object to be passed to an `InDims` constructor to define that the axis in `desc` shall participate in the inner function (i.e. shall be looped over), but inside the inner function `pre` values before and `after` values after the center value will be passed as well. 

For example passing `MovingWindow("Time", 2, 0)` will loop over the time axis and  always pass the current time step plus the 2 previous steps. So in the inner function the array will have an additional dimension of size 3.    
