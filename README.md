# snrest
Javascript wrapper for calling ServiceNow REST API.
Acts as an alternative for simple GlideAjax requests, reuquiering no server side code (script include).\\

## Usage
### Generate URL
to build the URL string use function 
```javascript
buildRequestString(inpObj)
```

### Execute request
To do a actual call to the current instance use restRequest(inpObj, callback)

Example:
```javascript
restRequest({table:"change_request",limit:2,query:"active=true"}, function(resp){ 
    console.log(resp)
});
```
This will dump the last 2 changes as JSON to the console.
Documentation will be expanded soon...

### inpObj definition
| Key  		  |Shortcut | Type   |Default              | Description                                                   |
|-----------|---------| ------ |---------------------|---------------------------------------------------------------|
| url  		  |u        | string | ''                  | Instance base url default empty when used in current instance |
| api  		  |a        | string | '/api/now/table/'   | Base url default empty                                        |
| table  		|t        | string | 'incident'          | Table or DB view to perform the operation on                  |
| fields    |f        | string | ''                  | A comma-separated list of fields to return in the response (all when empty)|
| view      |v        | string | ''                    | Render the response according to the specified UI view (overridden by fields)|
| query  		|q        | string | ''                  | An encoded query string used to filter the results            |
| values    |a        | array  | []                  | Values to replace in query ex: ['yes','maybe'] will replace<br />  answer={0}^answer={1} to answer=yes^answer=maybe|
| order  		|o        | string | '!sys_updated_on'   | Comma separated list of fields to order results by, to order descendant, preceed the field with a ! sign.|
| limit     |l        | int    | 10                  | The maximum number of results returned per page               |
| displayValue|d      | string | false               | Return the display value (true), actual value (false), or both (all) for reference fields|                 
| excludeReferenceLink|e| bool | true                | true to exclude Table API links for reference fields          |
| suppressPaginationHeader|s| bool | true            | true to supress pagination header          |
