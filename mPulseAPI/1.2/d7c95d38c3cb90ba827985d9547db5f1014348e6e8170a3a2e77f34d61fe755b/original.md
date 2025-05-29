Deletes an Alert object from the mPulse repository

At least one of `alertID` or `alertName` must be passed in to delete the alert object.

### Arguments

`token::AbstractString` :    The Repository authentication token fetched by calling [`getRepositoryToken`](@ref)

### Keyword Arguments

`alertID::Int64` :    The ID of the alert to update.

`alertName::AbstractString` :    The Alert name in mPulse. This is available from the mPulse domain configuration dialog.

### Returns

Returns true if the delete is successful, else false.

### Throws

`ArgumentError` :    if token is empty or alertID is empty

`mPulseAPIException` :    if API access failed for some reason
