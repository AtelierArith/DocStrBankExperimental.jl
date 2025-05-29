```
send!(lk::Link, m::Message)
send!(name::Symbol, m::Message)
```

Send a message `m` to an actor `lk` or `name` (if registered).
