Fetches an Alert object from the mPulse repository

At least one of `alertID` or `alertName` must be passed in to identify the alert. If neither are passed in, then all alerts for the tenant are returned.

The alert will be cached in memory for 1 hour, so subsequent calls using a matching `alertID` return quickly without calling out to the API.  This can be a problem if the alert changes in the repository. You can clear the cache for this tenant using [`mPulseAPI.clearAlertCache`](@ref) and passing in `alertID`.

### Arguments

`token::AbstractString` :    The Repository authentication token fetched by calling [`getRepositoryToken`](@ref)

### Keyword Arguments

`alertID::Int64` :    The ID of the alert to fetch.

`alertName::AbstractString` :    The Alert name in mPulse. This is available from the mPulse domain configuration dialog.

### Returns

`{Dict}` The `alert` object with the following fields:

`hidden::Bool` :    Flag indicating whether the alert is visible to the user

`parentID::Int64` :    The ID of the parent folder that this alert is in

`path::AbstractString` :    The folder path that this alert is in

`readOnly::Bool` :    Flag indicating whether the alert is able to be edited

`name::AbstractString` :    The alert's name

`tenantID::Int64` :    The ID of the tenant that the alert is in

`created::DateTime` :    The timestamp when this object was created

`id::Int64` :    The ID of the alert.

`description::AbstractString` :    The description of this alert entered into mPulse

`lastCached::DateTime` :    The timestamp when this object was last cached

`body::XMLElement` :    An XML object representing the alert's XML definition or an empty node if you do not have permission to see the full alert

`references::Dict` :    An array of `Dict`s with reference information such as `name`, `id`, `type`, and `path`.

`uid::AbstractString` :    The encrypted uid associated with the alert

`deleted::Bool` :    Flag indicating whether the alert has been deleted

`ownerID::Int64` :    The ID of the alert's owner

`attributes::Dict` :    A `Dict` containing whether the alert is active, version number, and the time(s) that the alert was last cleared, triggered, and updated.

`lastModified::DateTime` :    The timestamp when this object was created

### Throws

`ArgumentError` :    if token is empty or alertID is empty

`mPulseAPIException` :    if API access failed for some reason
