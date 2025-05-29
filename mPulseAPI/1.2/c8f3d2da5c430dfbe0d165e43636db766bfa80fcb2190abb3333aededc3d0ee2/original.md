Logs in to the mPulse repository and fetches an Authorization token that can be used for other calls

The token will be cached in memory for 5 hours, so subsequent calls using the same tenant will return quickly without calling out to the API.  This can be a problem if the account has signed in from a different location or is logged out of mPulse.  You can clear the cache for this token using [`mPulseAPI.clearTokenCache`](@ref)

### Arguments

`tenant::AbstractString` :    The name of the tenant to log in to. The token will be bound to this tenant.

`apiToken::AbstractString` :    The apiToken issued by mPulse that allows authenticating with the API. If you've      previously authenticated with this tenant, the `apiToken` will be cached and does      not need to be passed in again

### Returns

`{ASCIIString}` The mPulse Repository Auth token which may be used in the `X-Auth-Token` header for subsequent API calls

### Throws

`ArgumentError` :    if the tenant or apiToken are empty

`mPulseAPIAuthException` :    if authentication failed for some reason
