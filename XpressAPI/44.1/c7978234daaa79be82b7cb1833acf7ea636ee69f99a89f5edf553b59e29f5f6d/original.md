```
XPRS_ERRORCODE
```

The most recent Optimizer error number that occurred. (integer)

This is useful to determine the precise error or warning that has occurred, after an Optimizer function has signalled an error by returning a non-zero value. The return value itself is not the error number. Refer to the section for a list of possible error numbers, the errors and warnings that they indicate, and advice on what they mean and how to resolve them. A short error message may be obtained using XPRSgetlasterror, and all messages may be intercepted using the user output callback function; see XPRSaddcbmessage.
