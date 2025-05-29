Fetches a Domain object from the mPulse repository

To fetch a single domain, at least one of `domainID`, `appKey` or `appName` must be passed in to identify the domain. If none of these are passed in, then all domains that are readable by the specified `token` will be returned as an array.

The domain will be cached in memory for 1 hour, so subsequent calls using a matching `domainID`, `appKey` or `appName` return quickly without calling out to the API.  This can be a problem if the domain changes in the repository. You can clear the cache for this domain using [`mPulseAPI.clearDomainCache`](@ref) and passing in one of `domainID`, `appKey` or `appName`.

### Arguments

`token::AbstractString` :    The Repository authentication token fetched by calling [`getRepositoryToken`](@ref)

### Keyword Arguments

`domainID::Int64` :    The ID of the domain to fetch.  This is the fastest method, but it can be hard to figure out a domain's ID

`appKey::AbstractString` :    The App Key (formerly known as API key) associated with the domain.  This is available from the mPulse domain configuration dialog.

`appName::AbstractString` :    The App name in mPulse. This is available from the mPulse domain configuration dialog.

### Returns

`{Dict|Array{Dict}}` If one of `domainID`, `appKey` or `appName` are passed in, then a single `domain` object is returned as a `Dict`.

If none of these are passed in, then an array of all domains is returned, each is a `Dict`.

The `domain` `Dict` has the following fields:

`name` :    The app's name

`id::Int64` :    The app's ID

`body::XMLElement` :    An XML object representing the app's XML definition

`tenantID::Int64` :    The ID of the tenant that this app is in

`description::AbstractString` :    The description of this app entered into mPulse

`created::DateTime` :    The timestamp when this object was created

`lastModified::DateTime` :    The timestamp when this object was created

`attributes::Dict` :    A `Dict` of attributes for this app, including its `AppKey`

`custom_metrics::Dict` :    A `{Dict}` of Custom Metric names mapped to database fieldnames with the following structure:

```julia
Dict(
    <metric name> => Dict(
        "index"        => <index>,                      # Numeric index
        "fieldname"    => "custommetric<index>",        # Field name in dswb tables
        "lastModified" => <lastModifiedDate>,
        "description"  => "<description>",
        "dataType"     => Dict(
            "decimalPlaces"  => "2",
            "type"           => "<metric type>",
            "currencyCode"   => "<ISO 4217 Currency Code if type==Currency>"
        ),
        "colors"       => [<array of color HEX codes>]
    ),
    ...
)
```

`custom_timers::Dict` :    A `{Dict}` of Custom Timer names mapped to database fieldnames with the following structure:

```julia
Dict(
    <timer name> => Dict(
        "index"         => <index>,                      # Numeric index
        "fieldname"     => "customtimer<index>",         # Field name in dswb tables
        "mpulseapiname" => "CustomTimer<index>",
        "lastModified"  => <lastModifiedDate>,
        "description"   => "<description>",
        "colors"        => Array(
            Dict(
                "timingType"  => "<seconds | milliseconds>",
                "timingStart" => "<start timer value for this colour range>",
                "timingEnd"   => "<end timer value for this colour range>",
                "colorStart"  => "<start of this color range>",
                "endStart"    => "<end of this color range>"
            ),
            ...
        )
    ),
    ...
)
```

`session_timeout::Int64` :    The session timeout value in minutes

`resource_timing::Bool` :    Flag indicating whether resource timing collection is enabled or not

`vertical_market::AbstractString` :    The vertical market that this domain belongs to

### Throws

`ArgumentError` :    if token is empty or domainID, appKey and appName are all empty

`mPulseAPIException` :    if API access failed for some reason

`Exception` :    if something unexpected happened while parsing the repository object
