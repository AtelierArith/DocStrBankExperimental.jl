```
Message(m::String)
```

Create a message with a string as a buffer (for send). Note: the Message now "owns" the string, it must not be resized, or even written to after the message is sent.
