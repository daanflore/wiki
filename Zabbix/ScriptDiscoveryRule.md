# Script based discovery rule

First you need to create a discovery rule 

The type of the rule needs to be a zabbix script the script will prep the json to process it:
![scriptBasedDiscovery.png](.\scriptBasedDiscovery.png)


```javascript
var obj = JSON.parse(value);

const semanticModelId = obj.semanticModelId;
const workspaceId = obj.workspaceId;
const clientId = obj.clientId;
const clientSecret = obj.clientSecret;
const tenant = obj.tenant;

var httpRequestAgent = new HttpRequest();

// Get oauth2token
httpRequestAgent.addHeader('Content-Type: application/x-www-form-urlencoded');
const data = "grant_type=client_credentials&client_id=" + clientId + "&client_secret=" + clientSecret + "&scope=https://analysis.windows.net/powerbi/api/.default";
var response = httpRequestAgent.post("https://login.microsoftonline.com/" + tenant + "/oauth2/v2.0/token", data);

if (httpRequestAgent.getStatus() != 200) {
    throw 'Response code for authenticaiton: ' + httpRequestAgent.getStatus();
}

var jsonResponse = JSON.parse(response);
var accessToken = jsonResponse.access_token;

// Get datasets
httpRequestAgent.clearHeader();
httpRequestAgent.addHeader("Authorization: Bearer " + accessToken);
response = httpRequestAgent.get("https://api.powerbi.com/v1.0/myorg/groups/" + workspaceId + "/datasets/");

if (httpRequestAgent.getStatus() != 200) {
    throw 'Response code for dataset: ' + httpRequestAgent.getStatus();
}

jsonResponse = JSON.parse(response);
var apiDatasets = jsonResponse.value
var datasets = [];

for (var index = 0; index < apiDatasets.length; index++) {
    if (apiDatasets[index].isRefreshable === true) {
        datasets.push({
            id: apiDatasets[index].id,
            name: apiDatasets[index].name
        });
    }
}

return JSON.stringify(datasets);
```

Then we define a LLD macro, in the macro we define the keys and we use JSONPath to get the needed fields out of it.
We need to work with an array of objects so that the grouping is correct.
Currently we did not find how to do this with a preprocessing so we did it using the javascript.
The macro's you have defined here can be used in item prototypes.
![lldMacro.png](.\lldMacro.png)
