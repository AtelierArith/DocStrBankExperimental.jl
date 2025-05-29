```
receive!(lk; timeout=5.0)
receive!(lk, from; timeout=5.0)
receive!(lk, Msg; timeout=5.0)
receive!(lk, Msg, from; timeout=5.0)
```

Receive a message over a link `lk`.

If `Msg` or `from` are provided, `receive!` returns only a  matching message. Other messages in `lk` are restored to it in their previous order.

# Parameters

  * `lk::Link`: local or remote link over which the message is received,
  * `Msg::Type{<:Message}`: [`Message`](@ref) type,
  * `from::Link`: local or remote link of sender. If `from` is   provided, only messages with a `from` field can be matched.
  * `timeout::Real=5.0`: maximum waiting time in seconds.

      * If `timeout==0`, `lk` is scanned only for existing messages.
      * Set `timeout=Inf` if you don't want to timeout.

# Returns

  * received message or `Timeout()`.
