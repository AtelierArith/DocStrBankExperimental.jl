Deletes an StatisticalModel object from the mPulse repository

At least one of `statModelID` or `statModelName` must be passed in to delete the Statistical Model object.

### Arguments

`token::AbstractString` :    The Repository authentication token fetched by calling [`getRepositoryToken`](@ref)

### Keyword Arguments

`statModelID::Int64` :    The ID of the statistical model to update.

`statModelName::AbstractString` :    The statistical model name in mPulse. This is available from the mPulse domain configuration dialog.

### Returns

Returns true if the delete is successful, else false.

### Throws

`ArgumentError` :    if token is empty or statModelID is empty

`mPulseAPIException` :    if API access failed for some reason
