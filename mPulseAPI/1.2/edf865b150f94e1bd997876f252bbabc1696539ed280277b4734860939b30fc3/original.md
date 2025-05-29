Updates an Alert object from the mPulse repository

At least one of `alertID` or `alertName` must be passed in to update the alert object.

### Arguments

`token::AbstractString` :    The Repository authentication token fetched by calling [`getRepositoryToken`](@ref)

### Keyword Arguments

`alertID::Int64` :    The ID of the alert to update.

`alertName::AbstractString` :    The Alert name in mPulse. This is available from the mPulse domain configuration dialog.

`attributes::Dict` :    A `Dict` of alert attributes to update

`objectFields::Dict` :    A `Dict` of alert object fields to update

`body::AbstractString|LightXML.XMLElement=""` :    An XMLElement (if not empty) containing the body of the alert, containing pertinent information surrounding errors.

### Returns

`{Dict}` The updated `alert` object with the following fields:

`hidden::Bool` :    Flag indicating whether the alert is visible to the user

`parentID::Int64` :    The ID of the parent folder that this alert is in

`path::AbstractString` :    The folder path that this alert is in

`readOnly::Bool` :    Flag indicating whether the alert is able to be edited

`name::AbstractString` :    The alert's name

`tenantID::Int64` :    The ID of the tenant in which the alert is in

`created::DateTime` :    The timestamp when this object was created

`id::Int64` :    The ID of the alert.

`description::AbstractString` :    The description of this alert entered into mPulse

`lastCached::DateTime` :    The timestamp when this object was last cached

`errorXML::Union{AbstractString, LightXML.XMLElement}` :    An XML object representing the alert's XML error definition to be updated by the repository.

`references::Dict` :    An array of `Dict`s with reference information such as `name`, `id`, `type`, and `path`.

`uid::AbstractString` :    The encrypted uid associated with the alert

`deleted::Bool` :    Flag indicating whether the alert has been deleted

`ownerID::Int64` :    The ID of the alert's owner

`attributes::Dict` :    A `Dict` containing whether the alert is active, version number, and the time(s) that the alert was last cleared, triggered, and updated.

`lastModified::DateTime` :    The timestamp when this object was created

### Throws

`ArgumentError` :    if token is empty or alertID is empty

`mPulseAPIException` :    if API access failed for some reason
