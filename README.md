# snrest
Javascript wrapper for calling ServiceNow REST API.
Acts as an alternative for simple GlideAjax requests, reuquiering no server side code (script include).\\

## Usage
### Generate URL
to build the URL string use function buildRequestString(inpObj)

### Execute request
To do a actual call to the current instance use restRequest(inpObj, callback)

Example:
restRequest({table:"change_request",limit:2,query:"active=true"}, function(resp){ console.log(resp)});
This will dump the last 2 changes as JSON to the console.
Documentation will be expanded soon...
